# UpdateLoginProfile

调用UpdateLoginProfile修改指定RAM用户的控制台登录信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=UpdateLoginProfile&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateLoginProfile|要执行的操作。取值：UpdateLoginProfile。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|指定RAM用户的登录名称。 |
|Password|String|否|mypassword|RAM用户的控制台登录新密码。

 密码必须符合密码强度要求。 |
|PasswordResetRequired|Boolean|否|false|RAM用户在下次登录时是否必须重置密码。取值：

 -   true
-   false |
|MFABindRequired|Boolean|否|false|是否强制要求RAM用户开启多因素认证。取值：

 -   true：要求开启。RAM用户在下次登录时必须绑定多因素认证设备。
-   false：不要求开启。 |
|Status|String|否|Active|开启或禁用控制台密码登录。取值：

 -   Active：开启。
-   Inactive：禁用。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoginProfile|Struct| |控制台登录信息。 |
|MFABindRequired|Boolean|false|是否强制要求用户开启多因素认证。 |
|PasswordResetRequired|Boolean|false|RAM用户在下次登录时是否必须重置密码。 |
|Status|String|Active|开启或禁用控制台密码登录。 |
|UpdateDate|String|2020-10-14T07:48:41Z|更新时间。 |
|UserPrincipalName|String|test@example11.onaliyun.com|RAM用户的登录名称。 |
|RequestId|String|BCDB6A7F-2199-41D9-B577-4FA536A5ADE1|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=UpdateLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&Password=mypassword
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateLoginProfileResponse>
	  <RequestId>BCDB6A7F-2199-41D9-B577-4FA536A5ADE1</RequestId>
	  <LoginProfile>
		    <Status>Active</Status>
		    <UpdateDate>2020-10-14T07:48:41Z</UpdateDate>
		    <PasswordResetRequired>false</PasswordResetRequired>
		    <UserPrincipalName>test@example11.onaliyun.com</UserPrincipalName>
		    <MFABindRequired>false</MFABindRequired>
	  </LoginProfile>
</UpdateLoginProfileResponse>
```

`JSON` 格式

```
{
  "RequestId": "BCDB6A7F-2199-41D9-B577-4FA536A5ADE1",
  "LoginProfile": {
    "Status": "Active",
    "UpdateDate": "2020-10-14T07:48:41Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example11.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

