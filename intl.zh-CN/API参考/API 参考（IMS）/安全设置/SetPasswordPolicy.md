# SetPasswordPolicy

调用SetPasswordPolicy设置RAM用户密码强度策略。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=SetPasswordPolicy&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetPasswordPolicy|要执行的操作。取值：SetPasswordPolicy。 |
|MinimumPasswordLength|Integer|否|8|最小密码长度。

 取值范围8~32。默认值：8。 |
|RequireLowercaseCharacters|Boolean|否|false|密码中是否必须包含小写字母。取值：

 -   true
-   false（默认值） |
|RequireUppercaseCharacters|Boolean|否|false|密码中是否必须包含大写字母。取值：

 -   true
-   false（默认值） |
|RequireNumbers|Boolean|否|false|密码中是否必须包含数字。取值：

 -   true
-   false（默认值） |
|RequireSymbols|Boolean|否|false|密码中是否必须包含符号。取值：

 -   true
-   false（默认值） |
|HardExpire|Boolean|否|false|密码过期后是否限制登录。取值：

 -   true：密码过期后，不能登录控制台。需要通过主账号或具有管理员权限的RAM用户重置该RAM用户的密码后，才能正常登录。
-   false（默认值）：密码过期后，RAM用户可以自行更改密码，然后正常登录。 |
|MaxLoginAttemps|Integer|否|0|密码重试次数约束。连续输入错误密码达到设定次数后，账号将被锁定一小时。

 取值范围：0~32。

 默认值：0，表示不启用密码重试约束。 |
|PasswordReusePrevention|Integer|否|0|历史密码检查策略。

 禁止使用前N次的历史密码，N的取值范围：0~24。

 默认值：0，表示不启用历史密码检查策略。 |
|MaxPasswordAge|Integer|否|0|密码有效期。

 取值范围：0~1095。单位：天。

 默认值：0，表示永不过期。 |
|MinimumPasswordDifferentCharacter|Integer|否|0|密码中最少包含的不同字符数量。

 取值范围：0~8。

 默认值：0，表示不限制密码中的不同字符数量。 |
|PasswordNotContainUserName|Boolean|否|false|密码中是否不允许包含用户名。取值：

 -   true：密码中不能包含用户名。
-   false（默认值）：密码中可以包含用户名。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PasswordPolicy|Struct| |密码强度策略信息。 |
|HardExpire|Boolean|false|密码过期后是否限制登录。 |
|MaxLoginAttemps|Integer|0|密码重试次数约束。 |
|MaxPasswordAge|Integer|0|密码有效期。 |
|MinimumPasswordDifferentCharacter|Integer|0|密码中最少包含的不同字符数量。 |
|MinimumPasswordLength|Integer|8|最小密码长度。 |
|PasswordNotContainUserName|Boolean|false|密码中是否不允许包含用户名。 |
|PasswordReusePrevention|Integer|0|历史密码检查策略。 |
|RequireLowercaseCharacters|Boolean|false|密码中是否必须包含小写字母。 |
|RequireNumbers|Boolean|false|密码中是否必须包含数字。 |
|RequireSymbols|Boolean|false|密码中是否必须包含符号。 |
|RequireUppercaseCharacters|Boolean|false|密码中是否必须包含大写字母。 |
|RequestId|String|3FB5551F-B2ED-40D4-8392-1E4AC2384EFD|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=SetPasswordPolicy
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetPasswordPolicyResponse>
	  <RequestId>3FB5551F-B2ED-40D4-8392-1E4AC2384EFD</RequestId>
	  <PasswordPolicy>
		    <MinimumPasswordLength>8</MinimumPasswordLength>
		    <RequireLowercaseCharacters>false</RequireLowercaseCharacters>
		    <HardExpire>false</HardExpire>
		    <RequireNumbers>false</RequireNumbers>
		    <MaxLoginAttemps>0</MaxLoginAttemps>
		    <PasswordReusePrevention>0</PasswordReusePrevention>
		    <MaxPasswordAge>0</MaxPasswordAge>
		    <PasswordNotContainUserName>false</PasswordNotContainUserName>
		    <RequireUppercaseCharacters>false</RequireUppercaseCharacters>
		    <MinimumPasswordDifferentCharacter>0</MinimumPasswordDifferentCharacter>
		    <RequireSymbols>false</RequireSymbols>
	  </PasswordPolicy>
</SetPasswordPolicyResponse>
```

`JSON` 格式

```
{
  "RequestId": "3FB5551F-B2ED-40D4-8392-1E4AC2384EFD",
  "PasswordPolicy": {
    "MinimumPasswordLength": 8,
    "RequireLowercaseCharacters": false,
    "HardExpire": false,
    "RequireNumbers": false,
    "MaxLoginAttemps": 0,
    "PasswordReusePrevention": 0,
    "MaxPasswordAge": 0,
    "PasswordNotContainUserName": false,
    "RequireUppercaseCharacters": false,
    "MinimumPasswordDifferentCharacter": 0,
    "RequireSymbols": false
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

