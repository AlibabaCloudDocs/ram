# CreateLoginProfile

调用CreateLoginProfile开启指定RAM用户的控制台登录。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateLoginProfile&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoginProfile|要执行的操作。取值：CreateLoginProfile。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |
|Password|String|是|mypassword|RAM用户的控制台登录密码。

 密码必须符合密码强度要求。 |
|PasswordResetRequired|Boolean|否|false|RAM用户在下次登录时是否必须重置密码。取值：

 -   true
-   false（默认值） |
|MFABindRequired|Boolean|否|false|是否强制要求RAM用户开启多因素认证。取值：

 -   true：要求开启。RAM用户在下次登录时必须绑定多因素认证设备。
-   false（默认值）：不要求开启。 |
|Status|String|否|Active|开启或禁用控制台密码登录。取值：

 -   Active（默认值）：开启。
-   Inactive：禁用。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoginProfile|Struct| |控制台登录信息。 |
|MFABindRequired|Boolean|false|是否强制要求RAM用户开启多因素认证。 |
|PasswordResetRequired|Boolean|false|RAM用户在下次登录时是否必须重置密码。 |
|Status|String|Active|开启或禁用控制台密码登录。 |
|UpdateDate|String|2020-10-14T03:47:51Z|更新时间。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |
|RequestId|String|29CB303C-1F05-43A6-A6BC-EBC5A797F8DB|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&Password=mypassword
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateLoginProfileResponse>
	  <RequestId>29CB303C-1F05-43A6-A6BC-EBC5A797F8DB</RequestId>
	  <LoginProfile>
		    <Status>Active</Status>
		    <UpdateDate>2020-10-14T03:47:51Z</UpdateDate>
		    <PasswordResetRequired>false</PasswordResetRequired>
		    <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    <MFABindRequired>false</MFABindRequired>
	  </LoginProfile>
</CreateLoginProfileResponse>
```

`JSON` 格式

```
{
  "RequestId": "29CB303C-1F05-43A6-A6BC-EBC5A797F8DB",
  "LoginProfile": {
    "Status": "Active",
    "UpdateDate": "2020-10-14T03:47:51Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

