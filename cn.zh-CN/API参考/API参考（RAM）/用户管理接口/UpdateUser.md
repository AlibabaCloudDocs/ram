# UpdateUser

调用UpdateUser接口更新RAM用户的基本信息。

本文将提供一个示例，将RAM用户的名称由`zhangq****`修改为`xiaoq****`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateUser&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateUser|要执行的操作。取值：**UpdateUser**。 |
|UserName|String|是|zhangq\*\*\*\*|RAM用户名称。 |
|NewUserName|String|是|xiaoq\*\*\*\*|RAM用户的新名称。

 长度为1~64个字符，可包含英文字母、数字、半角句号（.）、短划线（-）和下划线（\_）。 |
|NewDisplayName|String|否|xiaoq\*\*\*\*|RAM用户的新显示名称。

 长度为1~128个字符。 |
|NewMobilePhone|String|否|86-1860000\*\*\*\*|RAM用户的新手机号码。

 格式：国际区号-号码。

 **说明：** 该参数仅适用于中国站。 |
|NewEmail|String|否|xiaoq\*\*\*\*@example.com|RAM用户的新电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|NewComments|String|否|This is a cloud computing engineer.|新备注。

 长度为1~128个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~28676~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|User|Object| |RAM用户信息。 |
|DisplayName|String|xiaoq\*\*\*\*|RAM用户的显示名称。 |
|Email|String|xiaoq\*\*\*\*@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|UpdateDate|String|2015-02-11T03:15:21Z|RAM用户的更新时间（UTC时间）。 |
|MobilePhone|String|86-1860000\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UserId|String|122748924538\*\*\*\*|RAM用户的唯一标识。 |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2015-01-23T12:33:18Z|RAM用户的创建时间（UTC时间）。 |
|UserName|String|xiaoq\*\*\*\*|RAM用户的名称。 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=UpdateUser
&UserName=zhangq****
&NewUserName=xiaoq****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateUserResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <User>
        <UserId>122748924538****</UserId>
        <UserName>xiaoq****</UserName>
        <DisplayName>xiaoq*****</DisplayName>
        <MobilePhone>86-1860000****</MobilePhone>
        <Email>xiaoq****@example.com</Email>
        <Comments>This is a cloud computing engineer.</Comments>
        <CreateDate>2015-01-23T12:33:18Z</CreateDate>
        <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
    </User>
</UpdateUserResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "04F0F334-1335-436C-A1D7-6C044FE73368",
  "User" : {
    "UserId" : "122748924538****",
    "UserName" : "xiaoq****",
    "DisplayName" : "xiaoq*****",
    "MobilePhone" : "86-1860000****",
    "Email" : "xiaoq****@example.com",
    "Comments" : "This is a cloud computing engineer.",
    "CreateDate" : "2015-01-23T12:33:18Z",
    "UpdateDate" : "2015-02-11T03:15:21Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

