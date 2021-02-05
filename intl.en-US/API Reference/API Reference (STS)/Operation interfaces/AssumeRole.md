# AssumeRole

Obtains a temporary identity to assume a RAM role. In this example, an Alibaba Cloud account is used as the trusted entity of the RAM role.

**Note:**

Security Token Service \(STS\) supports up to 6,000 AssumeRole API requests for each Alibaba Cloud account. API requests that are sent by using RAM users and RAM roles that belong to the Alibaba Cloud account are also counted. If the number of API requests exceeds 6,000, the following error message is returned:

```
Request was denied due to user flow control.
```

## Request parameters

|Parameter|Type|Required|Example|Description|
|:--------|:---|:-------|:------|:----------|
|Action|String|Yes|AssumeRole|The operation that you want to perform. Set the value to AssumeRole.|
|RoleArn|String|Yes|acs:ram::123456789012\*\*\*\*:role/adminrole|The Alibaba Cloud Resource Name \(ARN\) of the RAM role. Format: `acs:ram::$accountID:role/$roleName`. **Note:**

-   `$accountID`: specifies the ID of the Alibaba Cloud account that owns the RAM role. To view the account ID, log on to the Alibaba Cloud console, move the pointer over your profile picture in the upper-right corner of the page, and then click **Security Settings**.
-   `$roleName`: specifies the name of the RAM role. To view the RAM role name, perform the following steps: Log on to the RAM console. In the left-side navigation pane, click **RAM Roles**. On the page that appears, view the name of the RAM role in the **RAM Role Name** column. |
|RoleSessionName|String|Yes|alice|The customized role session name. This parameter can be used to identify the RAM user who assumes the RAM role.

The name must be 2 to 32 characters in length and can contain letters, digits, periods \(.\), at signs \(@\), hyphens \(-\), and underscores \(\_\). |
|Policy|String|No|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}|The policy that specifies the permissions of the returned STS token.

You can use this parameter to grant the STS token fewer permissions than those granted to the RAM role. If you do not specify this parameter, the returned STS token has all the permissions of the RAM role.

The value must be 1 to 1,024 characters in length. |
|DurationSeconds|Long|No|3600|The validity period. Unit: seconds.

Minimum value: 900. Maximum value: the value of the MaxSessionDuration parameter. Default value: 3600.

**Note:** You can call the CreateRole or UpdateRole operation to set the MaxSessionDuration parameter. For more information, see [CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md) and [UpdateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/UpdateRole.md). |

## Response parameters

|Parameter|Type|Example|Description|
|:--------|:---|:------|:----------|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|The ID of the request|
|Credentials| | |The access credentials.|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|The AccessKey ID.|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|The AccessKey secret.|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|The STS token.|
|└Expiration|String|2015-04-09T11:52:19Z|The time when the STS token expires.|
|AssumedRoleUser| | |The temporary identity that you use to assume the role.|
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/adminrole/alice|The ARN of the RAM role. Format: `acs:ram::$accountID:role/$roleName/$RoleSessionName`. **Note:**

-   `$accountID`: indicates the ID of the Alibaba Cloud account that owns the RAM role. To view the account ID, log on to the Alibaba Cloud console, move the pointer over your profile picture in the upper-right corner of the page, and then click **Security Settings**.
-   `$roleName`: the name of the RAM role. To view the RAM role name, perform the following steps: Log on to the RAM console. In the left-side navigation pane, click **RAM Roles**. On the page that appears, view the name in the **RAM Role Name** column. |
|└AssumedRoleId|String|34458433936495\*\*\*\*:alice|The ID of the temporary identity that you use to assume the role.|

## Examples

Sample requests

```
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
& <Common request parameters>
```

Sample responses

`XML` format

```
<AssumeRoleResponse>
    <RequestId>6894B13B-6D71-4EF5-88FA-F32781734A7F</RequestId>
    <AssumedRoleUser>
        <Arn>acs:ram::123456789012****:role/adminrole/alice</arn>
        <AssumedRoleId>34458433936495****:alice</AssumedRoleId>
    </AssumedRoleUser>
    <Credentials>
        <AccessKeyId>STS.L4aBSCSJVMuKg5U1****</AccessKeyId>
        <AccessKeySecret>wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK****</AccessKeySecret>
        <SecurityToken>********</SecurityToken>
        <Expiration>2015-04-09T11:52:19Z</Expiration>
    </Credentials>
</AssumeRoleResponse>
```

`JSON` format

```
{
    "Credentials": {
        "AccessKeyId": "STS.L4aBSCSJVMuKg5U1****",
        "AccessKeySecret": "wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK****",
        "Expiration": "2015-04-09T11:52:19Z",
        "SecurityToken": "********"
    },
    "AssumedRoleUser": {
        "Arn": "acs:ram::123456789012****:role/adminrole/alice",
        "AssumedRoleId":"34458433936495****:alice"
        },
    "RequestId": "6894B13B-6D71-4EF5-88FA-F32781734A7F"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidParameter|The parameter RoleArn is wrongly formed.|The error message returned because the ARN format of the RAM role is invalid.|
|400|InvalidParameter.RoleArn|The parameter RoleArn is wrongly formed.|The error message returned because the ARN format of the RAM role is invalid.|
|400|InvalidParameter.RoleSessionName|The parameter RoleSessionName is wrongly formed.|The error message returned because the format of the RoleSessionName parameter is invalid. The value must be 2 to 32 characters in length and can contain letters, digits, periods \(.\), at signs \(@\), hyphens \(-\), and underscores \(\_\).|
|400|InvalidParameter.DurationSeconds|The Min/Max value of DurationSeconds is 15min/1hr.|The error message returned because the value of the DurationSeconds parameter is invalid. The minimum value is 900, and the maximum value is equal to the value of the MaxSessionDuration parameter.|
|400|InvalidParameter.PolicyGrammar|The parameter Policy has not passed grammar check.|The error message returned because the syntax of the policy is invalid.|
|400|InvalidParameter.PolicySize|The size of Policy must be smaller than 1024 bytes.|The error message returned because the length of the specified policy string exceeds the upper limit. The policy string can be up to 1,024 bytes in length.|
|403|NoPermission|You are not authorized to do this action. You should be authorized by RAM.|The error message returned because the STS token does not have the required permissions. For more information about how to handle the error, see [FAQ about RAM roles and STS tokens](/intl.en-US/FAQ/FAQ about RAM roles and STS tokens.md).|
|404|EntityNotExist.Role|The specified Role not exists.|The error message returned because the specified RAM role does not exist.|
|500|InternalError|STS Server Internal Error happened.|The error message returned because an internal server error occurred.|

