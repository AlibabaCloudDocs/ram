# GetLoginProfile

调用GetLoginProfile查询指定RAM用户的控制台登录信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetLoginProfile&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetLoginProfile|要执行的操作。取值：GetLoginProfile。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoginProfile|Struct| |控制台登录信息。 |
|LastLoginTime|String|2020-10-14T07:25:25Z|上次登录控制台时间。 |
|MFABindRequired|Boolean|false|是否强制要求用户开启多因素认证。 |
|PasswordResetRequired|Boolean|false|RAM用户在下次登录时是否必须重置密码。 |
|Status|String|Active|开启或禁用控制台密码登录。 |
|UpdateDate|String|2020-10-14T06:56:45Z|更新时间。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |
|RequestId|String|E517F18B-632C-48FC-93F1-CDCBCC6F8444|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetLoginProfileResponse>
	  <RequestId>E517F18B-632C-48FC-93F1-CDCBCC6F8444</RequestId>
	  <LoginProfile>
		    <Status>Active</Status>
		    <LastLoginTime>2020-10-14T07:25:25Z</LastLoginTime>
		    <UpdateDate>2020-10-14T07:25:00Z</UpdateDate>
		    <PasswordResetRequired>false</PasswordResetRequired>
		    <UserPrincipalName>test@example11.onaliyun.com</UserPrincipalName>
		    <MFABindRequired>false</MFABindRequired>
	  </LoginProfile>
</GetLoginProfileResponse>
```

`JSON` 格式

```
{
  "RequestId": "E517F18B-632C-48FC-93F1-CDCBCC6F8444",
  "LoginProfile": {
    "Status": "Active",
    "LastLoginTime": "2020-10-14T07:25:25Z",
    "UpdateDate": "2020-10-14T07:25:00Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example11.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

