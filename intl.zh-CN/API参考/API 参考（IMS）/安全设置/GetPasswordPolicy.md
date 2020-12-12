# GetPasswordPolicy

调用GetPasswordPolicy查询RAM用户密码强度策略信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetPasswordPolicy&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetPasswordPolicy|要执行的操作。取值：GetPasswordPolicy。 |

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
|RequestId|String|BDAA8408-E67C-428B-BFF0-1B2AC05C9610|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetPasswordPolicy
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetPasswordPolicyResponse>
	  <RequestId>BDAA8408-E67C-428B-BFF0-1B2AC05C9610</RequestId>
	  <PasswordPolicy>
		    <MinimumPasswordLength>8</MinimumPasswordLength>
		    <HardExpire>false</HardExpire>
		    <RequireLowercaseCharacters>false</RequireLowercaseCharacters>
		    <RequireNumbers>false</RequireNumbers>
		    <MaxPasswordAge>0</MaxPasswordAge>
		    <MaxLoginAttemps>0</MaxLoginAttemps>
		    <PasswordReusePrevention>0</PasswordReusePrevention>
		    <PasswordNotContainUserName>false</PasswordNotContainUserName>
		    <RequireUppercaseCharacters>false</RequireUppercaseCharacters>
		    <MinimumPasswordDifferentCharacter>0</MinimumPasswordDifferentCharacter>
		    <RequireSymbols>false</RequireSymbols>
	  </PasswordPolicy>
</GetPasswordPolicyResponse>
```

`JSON` 格式

```
{
  "RequestId": "BDAA8408-E67C-428B-BFF0-1B2AC05C9610",
  "PasswordPolicy": {
    "MinimumPasswordLength": 8,
    "HardExpire": false,
    "RequireLowercaseCharacters": false,
    "RequireNumbers": false,
    "MaxPasswordAge": 0,
    "MaxLoginAttemps": 0,
    "PasswordReusePrevention": 0,
    "PasswordNotContainUserName": false,
    "RequireUppercaseCharacters": false,
    "MinimumPasswordDifferentCharacter": 0,
    "RequireSymbols": false
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

