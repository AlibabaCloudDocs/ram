# CreateUser

调用CreateUser创建RAM用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateUser&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUser|要执行的操作。取值：CreateUser。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。

 格式为`<username>@<AccountAlias>.onaliyun.com`，其中`<username>`为RAM用户名称，`<AccountAlias>.onaliyun.com`为默认域名。

 `UserPrincipalName`总长度为1~128个字符，其中`<username>`的长度为1~64个字符。可包含英文字母、数字、英文句点（.）、at（@）、短划线（-）和下划线（\_）。 |
|DisplayName|String|是|test|RAM用户的显示名称。

 长度为1~24个字符。 |
|MobilePhone|String|否|86-1868888\*\*\*\*|RAM用户的手机号码。

 格式：国际区号-号码。

 **说明：** 该参数仅适用于中国站。 |
|Email|String|否|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|Comments|String|否|This is a cloud computing engineer.|备注。

 长度为1~128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2BB8C44A-2862-4922-AD43-03924749173B|请求ID。 |
|User|Struct| |RAM用户信息。 |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2020-10-12T09:12:00Z|RAM用户的创建时间。 |
|DisplayName|String|test|RAM用户的显示名称。 |
|Email|String|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|LastLoginDate|String|2020-10-12T09:12:00Z|RAM用户最近一次登录控制台的时间。 |
|MobilePhone|String|86-1868888\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UpdateDate|String|2020-10-12T09:12:00Z|RAM用户的更新时间。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateUser
&UserPrincipalName=test@example.onaliyun.com
&DisplayName=test
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateUserResponse>
	  <User>
		    <UpdateDate>2020-10-12T09:12:00Z</UpdateDate>
		    <Email>alice@example.com</Email>
		    <Comments>This is a cloud computing engineer.</Comments>
		    <UserId>20732900249392****</UserId>
		    <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
		    <DisplayName>test</DisplayName>
		    <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    <CreateDate>2020-10-12T09:12:00Z</CreateDate>
		    <MobilePhone>86-1868888****</MobilePhone>
	  </User>
	  <RequestId>2BB8C44A-2862-4922-AD43-03924749173B</RequestId>
</CreateUserResponse>
```

`JSON` 格式

```
{
  "User": {
    "UpdateDate": "2020-10-12T09:12:00Z",
    "Email": "alice@example.com",
    "Comments": "This is a cloud computing engineer.",
    "UserId": "20732900249392****",
    "LastLoginDate": "2020-10-12T09:12:00Z",
    "DisplayName": "test",
    "UserPrincipalName": "test@example.onaliyun.com",
    "CreateDate": "2020-10-12T09:12:00Z",
    "MobilePhone": "86-1868888****"
  },
  "RequestId": "2BB8C44A-2862-4922-AD43-03924749173B"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

