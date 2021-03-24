# UpdateUser

调用UpdateUser修改RAM用户信息。

本文将提供一个示例，修改RAM用户`test@example.onaliyun.com`的名称为`new@example.onaliyun.com`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=UpdateUser&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateUser|要执行的操作。取值：UpdateUser。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|指定的RAM用户登录名称。

 **说明：** `UserPrincipalName`与`UserId`参数，必须指定一个，但不能同时指定。 |
|UserId|String|否|20732900249392\*\*\*\*|指定的RAM用户ID。

 **说明：** `UserPrincipalName`与`UserId`参数，必须指定一个，但不能同时指定。 |
|NewUserPrincipalName|String|否|new@example.onaliyun.com|RAM用户的新登录名称。

 格式为`<username>@<AccountAlias>.onaliyun.com`，其中`<username>`为RAM用户名称，`<AccountAlias>.onaliyun.com`为默认域名。

 `UserPrincipalName`长度为1~128个字符，可包含英文字母、数字、半角句号（.）、短划线（-）和下划线（\_）。其中`<username>`的长度为1~64个字符。 |
|NewDisplayName|String|否|new|RAM用户的新显示名称。

 长度为1~24个字符。 |
|NewMobilePhone|String|否|86-1868888\*\*\*\*|RAM用户的新手机号码。

 格式：国际区号-号码。

 **说明：** 该参数仅适用于中国站。 |
|NewEmail|String|否|alice@example.com|RAM用户的新电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|NewComments|String|否|This is a cloud computing engineer.|新备注。

 长度为1~128个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~187377~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|1B56DD42-6962-4F89-A19C-079EED1F0FE3|请求ID。 |
|User|Struct| |RAM用户信息。 |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2020-10-12T09:12:00Z|RAM用户的创建时间。 |
|DisplayName|String|new|RAM用户的显示名称。 |
|Email|String|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|LastLoginDate|String|2020-10-12T09:12:00Z|RAM用户最近一次登录控制台的时间。 |
|MobilePhone|String|86-1868888\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UpdateDate|String|2020-10-13T09:19:49Z|RAM用户的更新时间。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|new@example.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=UpdateUser
&UserPrincipalName=test@example.onaliyun.com
&NewUserPrincipalName=new@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateUserResponse>
	  <User>
		    <UpdateDate>2020-10-13T09:19:49Z</UpdateDate>
		    <Email>alice@example.com</Email>
		    <Comments>This is a cloud computing engineer.</Comments>
		    <UserId>20732900249392****</UserId>
		    <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
		    <DisplayName>new</DisplayName>
		    <UserPrincipalName>new@example.onaliyun.com</UserPrincipalName>
		    <CreateDate>2020-10-12T09:12:00Z</CreateDate>
		    <MobilePhone>86-1868888****</MobilePhone>
	  </User>
	  <RequestId>1B56DD42-6962-4F89-A19C-079EED1F0FE3</RequestId>
</UpdateUserResponse>
```

`JSON`格式

```
{
  "User": {
    "UpdateDate": "2020-10-13T09:19:49Z",
    "Email": "alice@example.com",
    "Comments": "This is a cloud computing engineer.",
    "UserId": "20732900249392****",
    "LastLoginDate": "2020-10-12T09:12:00Z",
    "DisplayName": "new",
    "UserPrincipalName": "new@example.onaliyun.com",
    "CreateDate": "2020-10-12T09:12:00Z",
    "MobilePhone": "86-1868888****"
  },
  "RequestId": "1B56DD42-6962-4F89-A19C-079EED1F0FE3"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

