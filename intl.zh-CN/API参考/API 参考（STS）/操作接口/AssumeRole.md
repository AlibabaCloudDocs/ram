# AssumeRole

调用AssumeRole接口获取一个扮演该角色的临时身份，此处RAM用户扮演的是受信实体为阿里云账号类型的RAM角色。

**说明：**

AssumeRole接口调用次数限制：每分钟最多调用6000次，且一个阿里云账号及该账号下的RAM用户、RAM角色共用这6000次。当请求量超过6000次时，超出部分会报错，报错信息如下：

```
Request was denied due to user flow control.
```

## 请求参数

|名称|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|AssumeRole|要执行的操作。取值：AssumeRole|
|RoleArn|String|是|acs:ram::123456789012\*\*\*\*:role/adminrole|指定角色的ARN。格式：`acs:ram::$accountID:role/$roleName` 。 **说明：**

-   `$accountID`：阿里云账号ID。您可以通过登录阿里云控制台，将鼠标悬停在右上角头像的位置，单击**安全设置**进行查看。
-   `$roleName`：RAM角色名称。您可以通过登录RAM控制台，单击左侧导航栏的**RAM角色管理**，在**RAM角色名称**列表下进行查看。 |
|RoleSessionName|String|是|alice|用户自定义参数。此参数用来区分不同的令牌，可用于用户级别的访问审计。

长度为2~32个字符，可包含英文字母、数字、英文句点（.）、at（@）、短划线（-）和下划线（\_）。 |
|Policy|String|否|\{"Statement": \[\{"Action": \["\*"\],"Effect": "Allow","Resource": \["\*"\]\}\],"Version":"1"\}|权限策略。

生成STS Token时可以指定一个额外的权限策略，以进一步限制STS Token的权限。若不指定则返回的Token拥有指定角色的所有权限。

长度为1~1024个字符。 |
|DurationSeconds|Long|否|3600|过期时间，单位为秒。

过期时间最小值为900秒，最大值为MaxSessionDuration设置的时间。默认值为3600秒。

**说明：** 您可以通过CreateRole或UpdateRole接口设置角色最大会话时间MaxSessionDuration。详情请参见[CreateRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/CreateRole.md)或[UpdateRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/UpdateRole.md)。 |

## 返回数据

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|RequestId|String|6894B13B-6D71-4EF5-88FA-F32781734A7F|请求ID。|
|Credentials| | |访问凭证。|
|└AccessKeyId|String|STS.L4aBSCSJVMuKg5U1\*\*\*\*|访问密钥标识。|
|└AccessKeySecret|String|wyLTSmsyPGP1ohvvw8xYgB29dlGI8KMiH2pK\*\*\*\*|访问密钥。|
|└SecurityToken|String|\*\*\*\*\*\*\*\*|安全令牌。|
|└Expiration|String|2015-04-09T11:52:19Z|失效时间。|
|AssumedRoleUser| | |角色扮演临时身份。|
|└Arn|String|acs:ram::123456789012\*\*\*\*:role/adminrole/alice|指定角色的ARN。格式：`acs:ram::$accountID:role/$roleName/$RoleSessionName` 。 **说明：**

-   `$accountID`：阿里云账号ID。您可以通过登录阿里云控制台，将鼠标悬停在右上角头像的位置，单击**安全设置**进行查看。
-   `$roleName`：RAM角色名称。您可以通过登录RAM控制台，单击左侧导航栏的**RAM角色管理**，在**RAM角色名称**列表下进行查看。 |
|└AssumedRoleId|String|34458433936495\*\*\*\*:alice|该角色临时身份的用户ID。|

## 示例

请求示例

```
https://sts.aliyuncs.com?Action=AssumeRole
&RoleArn=acs:ram::123456789012****:role/adminrole
&RoleSessionName=alice
&DurationSeconds=3600
&Policy=<url_encoded_policy>
&<公共请求参数>
```

返回示例

`XML`格式

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

`JSON`格式

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

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|The parameter RoleArn is wrongly formed.|角色ARN格式错误。|
|400|InvalidParameter.RoleArn|The parameter RoleArn is wrongly formed.|角色ARN格式错误。|
|400|InvalidParameter.RoleSessionName|The parameter RoleSessionName is wrongly formed.|RoleSessionName格式错误，支持输入2~32个字符，请输入至少2个字符，允许输入英文字母、数字、英文句点（.）、at（@）、短划线（-）和下划线（\_）。|
|400|InvalidParameter.DurationSeconds|The Min/Max value of DurationSeconds is 15min/1hr.|DurationSeconds参数设置错误，过期时间最小值为900秒，最大值为MaxSessionDuration设置的时间。|
|400|InvalidParameter.PolicyGrammar|The parameter Policy has not passed grammar check.|权限策略语法错误。|
|400|InvalidParameter.PolicySize|The size of Policy must be smaller than 1024 bytes.|权限策略长度超限，最大不超过1024字符。|
|403|NoPermission|You are not authorized to do this action. You should be authorized by RAM.|STS Token没有权限。解决方法请参见[为什么使用STS时会报错](/intl.zh-CN/常见问题/RAM角色和STS Token常见问题.md)。|
|404|EntityNotExist.Role|The specified Role not exists.|指定的RAM角色不存在。|
|500|InternalError|STS Server Internal Error happened.|服务器内部错误。|

