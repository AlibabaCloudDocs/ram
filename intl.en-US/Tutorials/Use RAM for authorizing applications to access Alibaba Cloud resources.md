# Use RAM for authorizing applications to access Alibaba Cloud resources

This topic describes how to use a Security Token Service \(STS\) token of a Resource Access Management \(RAM\) role for authorizing applications to access Alibaba Cloud resources.

An enterprise has purchased Elastic Compute Service \(ECS\) instances and wants to deploy its applications on these ECS instances. To allow the applications to use AccessKey pairs to call the operations of other Alibaba Cloud services,

the enterprise can use one of the following methods:

-   Includes the AccessKey pairs in application code.
-   Saves the AccessKey pairs in the configuration files of the applications.

However, if the preceding methods are used, the following issues occur:

-   AccessKey pair disclosure: If AccessKey pairs are stored in the ECS instances in plaintext, the AccessKey pairs may be disclosed after snapshots and images are shared or ECS instances are created from images.
-   Complex O&M: The AccessKey pairs are stored in the ECS instances. If the AccessKey pairs are changed due to AccessKey pair rotations or user identity changes, all ECS instances and images must be updated and redeployed. This increases the difficulties in managing the ECS instances and images.

## Solution

To resolve the preceding issues, the enterprise can use an integrated feature of RAM to manage the permissions of ECS instances. This feature allows the enterprise to create a RAM role for each ECS instance and attach the required policies to each RAM role. The applications can use an STS token of the specific RAM role to call Alibaba Cloud operations.

![Use RAM for authorizing applications to access Alibaba Cloud resources](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6580549951/p14410.png)

## Process

1.  The enterprise creates a RAM role named MyApplicationRole.

    **Note:** **Alibaba Cloud Service** is selected as the trusted entity, and **Elastic Compute Service** is selected as the trusted service. This allows ECS to assume the RAM role and access Alibaba Cloud resources.

    For more information, see [Create a RAM role for a trusted Alibaba Cloud service](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md).

2.  The enterprise attaches the required policies to the RAM role.

    For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

    **Note:** If the STS token lacks permissions, the enterprise must attach the required policies to the RAM role. After the policies are attached, the permissions that are attached to the STS token immediately take effect without the need to restart the specific ECS instance.

3.  The enterprise uses its Alibaba Cloud account to create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

4.  The enterprise attaches the required policies to the RAM user.

    -   If the RAM user has the same responsibilities as an administrator, the `AdministratorAccess` policy must be attached to the RAM user.
    -   If the RAM user has different responsibilities from those of an administrator, the enterprise must create the following custom policy in the RAM console and attaches the policy to the RAM user:

        ```
        {
           "Statement": [
            {
              "Effect": "Allow",
              "Action": "ram:PassRole",
              "Resource": "acs:ram:*:*:role/MyApplicationRole" //Replace MyApplicationRole with the name of the RAM role.
            }
          ],
          "Version": "1"
        }                
        ```

        **Note:**

        -   Only authorized RAM users can create RAM roles for ECS instances. This prevents abuse of RAM roles.
        -   When a RAM user that can only manage ECS instances attempts to create an ECS instance and configure a RAM role, ECS checks whether the RAM user has the `ram:PassRole` policy on the RAM role. If the RAM user does not have the policy, the ECS instance fails to be created.
    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).

5.  The RAM user starts the ECS instance and configures the RAM role.

6.  ECS calls the STS [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation to obtain the STS token of the RAM role.

    **Note:** The STS service verifies the identity of ECS and the policies attached to the RAM role. If the verification succeeds, an STS token is issued. If the verification fails, the request is denied.

    For more information, see [Use an instance RAM role by calling API operations](/intl.en-US/Security/Instance RAM roles/Use an instance RAM role by calling API operations.md).

7.  The STS service returns the STS token to ECS.

8.  ECS includes the STS token in the metadata of the ECS instance and sends the metadata to the application deployed on the ECS instance.

    -   In a Linux system, applications can query the instance metadata to obtain an STS token and its validity period. For more information, see [Use RAM roles to access other Alibaba Cloud services](/intl.en-US/Best Practices/Use RAM roles to access other Alibaba Cloud services.md).

        Sample request

        ```
        curl http://100.100.100.200/latest/meta-data/ram/security-credentials/MyApplicationRole
        ```

        Sample response

        ```
        {
            "AccessKeyId": "STS.J8XXXXXXXXXX4",
            "AccessKeySecret": "9PjfXXXXXXXXXBf2XAW",
            "Expiration": "2017-06-09T09:17:19Z",
            "SecurityToken": "CAIXXXXXXXXXXXwmBkleCTkyI+",
            "LastUpdated": "2017-06-09T03:17:18Z",
            "Code": "Success"
        }
        ```

    -   If the applications use an Alibaba Cloud SDK, the SDK can automatically obtain the STS token of the RAM role from the ECS instance metadata. No AccessKey pair-related configurations are required in the SDK. For more information, see [Configure RamRole to achieve non-AK access to ECS instances]().

        **Note:** The applications can call Alibaba Cloud operations when the STS token is valid. The STS token expires one hour later. Before the STS token expires, it is updated by ECS.

9.  The applications use the STS token to call Alibaba Cloud operations.


**Note:** Applications deployed on other Alibaba Cloud services such as Function Compute and MaxCompute can also use STS tokens of RAM roles to call Alibaba Cloud operations.

