# UpdateUser

调用UpdateUser接口更新RAM用户的基本信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateUser&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateUser|要执行的操作。取值：UpdateUser。 |
|UserName|String|是|zhangq\*\*\*\*|RAM用户名称。 |
|NewUserName|String|否|xiaoq\*\*\*\*|新的RAM用户名称。

 长度为1~64个字符，可包含英文字母、数字、英文句点（.）、短划线（-）和下划线（\_）。 |
|NewMobilePhone|String|否|86-1860000\*\*\*\*|RAM用户的新手机号。

 格式：国际区号-号码。 |
|NewDisplayName|String|否|xiaoq\*\*\*\*|RAM用户的新显示名称。

 长度为1~128个字符或汉字，可包含英文字母、数字、英文句点（.）、at（@）、短划线（-）和空格。 |
|NewEmail|String|否|xiaoq\*\*\*\*@example.com|RAM用户的新邮箱。 |
|NewComments|String|否|这是一位云计算工程师|新备注。

 长度为1~128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |
|User|Struct| |RAM用户信息。 |
|Comments|String|这是一位云计算工程师|备注。 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。 |
|DisplayName|String|xiaoq\*\*\*\*|RAM用户显示名称。 |
|Email|String|xiaoq\*\*\*\*@example.com|RAM用户邮箱。 |
|MobilePhone|String|86-1860000\*\*\*\*|RAM用户手机号。 |
|UpdateDate|String|2015-02-11T03:15:21Z|更新时间。 |
|UserId|String|122748924538\*\*\*\*|RAM用户唯一标识。 |
|UserName|String|xiaoq\*\*\*\*|RAM用户名称。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=UpdateUser
&UserName=zhangq****
&NewUserName=xiaoq****
&NewMobilePhone=86-1860000****
&NewEmail=xiaoq****@example.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
<User>
    <UserId>122748924538****</UserId>
    <UserName>xiaoq****</UserName>
    <DisplayName>xiaoq*****</DisplayName>
    <MobilePhone>86-1860000****</MobilePhone>
    <Email>xiaoq****@example.com</Email>
    <Comments>这是一位云计算工程师</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
</User>
```

`JSON` 格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "User": {
        "UserId": "122748924538****",
        "UserName": "xiaoq****",
        "DisplayName": "xiaoq*****",
        "MobilePhone": "86-1860000****",
        "Email": "xiaoq****@example.com",
        "Comments": "这是一位云计算工程师",
        "CreateDate": "2015-01-23T12:33:18Z",
        "UpdateDate": "2015-02-11T03:15:21Z"
    }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ram)查看更多错误码。

