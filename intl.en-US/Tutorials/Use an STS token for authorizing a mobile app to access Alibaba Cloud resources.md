# Use an STS token for authorizing a mobile app to access Alibaba Cloud resources

This topic describes how to use a Security Token Service \(STS\) token of a Resource Access Management \(RAM\) role for authorizing a mobile app to access Alibaba Cloud resources.

An enterprise develops a mobile app and activates Object Storage Service \(OSS\). The mobile app runs on mobile devices. These mobile devices are not controlled by the enterprise. The enterprise must grant the necessary permissions to the mobile app. Then, the mobile app can upload data to and download data from OSS.

The enterprise has the following requirements:

-   Direct data transmission: The mobile app directly uploads data to or downloads data from OSS. The application server of the enterprise does not need to transfer data between the mobile app and OSS.
-   Security control: AccessKey pairs are not saved on mobile devices. Mobile devices are controlled by app users and cannot provide trusted operating environments.
-   Risk control: Security risks are minimized. During direct access to OSS, each app client is authorized based on the principle of least privilege, and the access duration is under strict control.

## Solution

Before a mobile app can directly upload data to or download data from OSS, the mobile app must apply for an access credential from the application server. After the application server receives the request, the server uses a RAM user identity to call the STS AssumeRole operation. If the call succeeds, the application receives an STS token and forwards the STS token to the mobile app. Then, the mobile app can use the STS token to access OSS.

![Authorize a mobile app to access Alibaba Cloud resources](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5580549951/p14407.png)

1.  The mobile app requests an STS token from the application server.

2.  The enterprise uses its Alibaba Cloud account to create a RAM role and attaches the required policies to the role.

    For more information, see [Create a RAM role and attach the required policies to the role](#section_04).

3.  The enterprise uses its Alibaba Cloud account to create a RAM user for the application server and allows the application server to assume the RAM role.

    For more information, see [Create a RAM user and allow the user to assume a RAM role](#section_xsw_quq_4p3).

4.  The application server calls the STS [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation to obtain an STS token of the RAM role.

    For more information, see [Obtain an STS token of the RAM role](#section_552_rvk_wrb).

5.  The application server can request an STS token that has fewer permissions than the policies attached to the RAM role. This way, the application server controls the access from the mobile app to OSS.

    For more information, see [Request an STS token that has fewer permissions than the policies attached to the RAM role](#section_e6m_2ec_my4).

6.  The mobile app uses the STS token to directly upload data to or download data from OSS.

    For more information, see [Use the STS token to access OSS](#section_05).


## Create a RAM role and attach the required policies to the role

The ID of the Alibaba Cloud account that is used by the enterprise in this section is `123456789012****`.

1.  The enterprise uses its Alibaba Cloud account to create a RAM role named `oss-readonly`. **Alibaba Cloud Account** is selected as the trusted entity type.

    **Note:** When the RAM role is created, the **Current Alibaba Cloud Account** is selected as the trusted account. This ensures that only RAM users that belong to the account can assume the RAM role.

    For more information, see [Create a RAM role for a trusted Alibaba Cloud account](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud account.md).

    After the RAM role is created, the enterprise can view the information about the role on the basic information page.

    -   In this example, the Alibaba Cloud Resource Name \(ARN\) of the RAM role is `acs:ram::123456789012****:role/oss-readonly`.
    -   The following policy is attached to the RAM role:

        **Note:** This policy indicates that only RAM users that belong to the Alibaba Cloud account of the enterprise can assume the RAM role.

        ```
        {
            "Statement": [{
                "Action": "sts:AssumeRole",
                "Effect": "Allow",
                "Principal": {
                    "RAM": [
                        "acs:ram::123456789012****:root"
                    ]
                }
            }],
            "Version": "1"
        }
        ```

2.  The enterprise uses its Alibaba Cloud account to attach the `AliyunOSSReadOnlyAccess` policy to the RAM role `oss-readonly`. The AliyunOSSReadOnlyAccess policy indicates the read-only permissions on OSS.

    For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).


## Create a RAM user and allow the user to assume a RAM role

1.  The enterprise uses its Alibaba Cloud account to create a RAM user named `appserver`.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  The enterprise uses its Alibaba Cloud account to attach the `AliyunSTSAssumeRoleAccess` policy to the RAM user. Then, the RAM user can assume the RAM role.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Obtain an STS token of the RAM role

1.  The application server uses the AccessKey pair of the RAM user to call the STS AssumeRole operation.

    **Note:** The AccessKey pair of the RAM user rather than the Alibaba Cloud account must be used.

    The following example shows how to use Alibaba Cloud CLI to call the AssumeRole operation:

    -   Sample request

        ```
        aliyuncli sts AssumeRole --RoleArn acs:ram::123456789012****:role/oss-readonly --RoleSessionName client-001
        ```

    -   Sample response

        ```
        {
             "AssumedRoleUser": {
                 "AssumedRoleId": "391578752573****:client-001", 
                 "Arn": "acs:ram::123456789012****:role/oss-readonly/client-001"
             }, 
             "Credentials": {
                 "AccessKeySecret": "93ci2umK1QKNEja6WGqi1Ba7Q2Fv9PwxZqtVF2Vy****", 
                 "SecurityToken": "********", 
                 "Expiration": "2016-01-13T15:02:37Z", 
                 "AccessKeyId": "STS.F13GjskXTjk38dBY6YxJt****"
             }, 
             "RequestId": "E1779AAB-E7AF-47D6-A9A4-53128708B6CE"
         }
        ```

    **Note:** In this example, the returned STS token has all policies of the RAM role `oss-readonly` because the `Policy` parameter is unspecified. The application server can also request an STS token that has fewer permissions than the policies attached to the RAM role. For more information, see [Request an STS token that has fewer permissions than the policies attached to the RAM role](#section_e6m_2ec_my4).

2.  The STS service sends the STS token to the application server. The STS token contains the following elements: `AccessKeyId`, `AccessKeySecret`, and `SecurityToken`.

    **Note:** The STS token `SecurityToken` is valid only for a short period of time. If the mobile app requires access to OSS for a long period of time, the application server must request a new STS token on a regular basis. For example, the application server can request a new STS token every 1,800 seconds.


## Request an STS token that has fewer permissions than the policies attached to the RAM role

In actual scenarios, we recommend that you specify the `Policy` parameter to grant the STS token with fewer permissions than the policies that are attached to the RAM role. Follow the principle of least privilege. The following example shows how to specify the Policy parameter:

In this example, the returned STS token has the permissions to access only objects that match the `sample-bucket/2015/01/01/*.jpg` pattern.

-   Sample request

    ```
    aliyuncli sts AssumeRole --RoleArn acs:ram::123456789012****:role/oss-readonly --RoleSessionName client-002 --Policy "{\"Version\":\"1\", \"Statement\": [{\"Effect\":\"Allow\", \"Action\":\"oss:GetObject\", \"Resource\":\"acs:oss:*:*:sample-bucket/2015/01/01/*.jpg\"}]}"
    ```

-   Sample response

    ```
    {
       "AssumedRoleUser": {
           "AssumedRoleId": "391578752573****:client-002", 
           "Arn": "acs:ram::123456789012****:role/oss-readonly/client-002"
       }, 
       "Credentials": {
           "AccessKeySecret": "28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7x****", 
           "SecurityToken": "********", 
           "Expiration": "2016-01-13T15:03:39Z", 
           "AccessKeyId": "STS.FJ6EMcS1JLZgAcBJSTDG1****"
       }, 
       "RequestId": "98835D9B-86E5-4BB5-A6DF-9D3156ABA567"
    }
    ```


**Note:** The default validity period of the STS token is 3,600 seconds. The enterprise can specify the `DurationSeconds` parameter to limit the validity period of the STS token. The maximum validity period of the STS token is 3,600 seconds.

## Use the STS token to access OSS

1.  The application server sends the STS token to the mobile app.

2.  The mobile app uses the STS token to access OSS.

    The following example shows how to use Alibaba Cloud CLI and the STS token to access an OSS object:

    -   Specify the STS token

        Syntax: `aliyuncli oss Config --host --accessid --accesskey --sts_token`.

        ```
        aliyuncli oss Config --host oss.aliyuncs.com --accessid STS.FJ6EMcS1JLZgAcBJSTDG1**** --accesskey 28Co5Vyx2XhtTqj3RJgdud4ntyzrSNdUvNygAj7x**** --sts_token CAESnQMIARKAASJgnzMzlXVyJn4KI+FsysaIpTGm8ns8Y74HVEj0pOevO8ZWXrnnkz4a4rBEPBAdFkh3197GUsprujsiU78FkszxhnQPKkQKcyvPihoXqKvuukrQ/Uoudk31KAJEz5o2EjlNUREcxWjRDRSISMzkxNTc4NzUyNTczOTcyODU0KgpjbGllbnQtMDAxMKmZxIHBKjoGUnNhTUQ1Qn8KATEaegoFQWxsb3cSJwoMQWN0aW9uRXF1YWxzEgZBY3Rpb24aDwoNb3NzOkdldE9iamVjdBJICg5SZXNvdXJjZUVxdWFscxIIUmVzb3VyY2UaLAoqYWNzOm9zczoqOio6c2FtcGxlLWJ1Y2tldC8yMDE1LzAxLzAxLyouanBnSgU0MzI3NFIFMjY4NDJaD0Fzc3VtZWRSb2xlVXNlcmAAahIzOTE1Nzg3NTI1NzM5NzI4NTRyCWVjcy1hZG1pbnjgxt7Cj/bo****
        ```

    -   Access OSS

        ```
        aliyuncli oss Get oss://sample-bucket/2015/01/01/grass.jpg
        ```


**Related topics**  


[Set up direct data transfer for mobile apps](/intl.en-US/Best Practices/Application server/Set up direct data transfer for mobile apps.md)

[Set up upload callback for mobile apps](/intl.en-US/Best Practices/Application server/Set up upload callback for mobile apps.md)

[Access OSS with a temporary access credential provided by STS](/intl.en-US/Developer Guide/Data security/Access and control/Access OSS with a temporary access credential provided by STS.md)

