# CreateUser

调用CreateUser接口创建RAM用户。

本文将提供一个示例，创建一个名为`alice`的RAM用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=CreateUser&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUser|要执行的操作。取值：**CreateUser**。 |
|UserName|String|是|alice|RAM用户的名称。

 长度为1~64个字符，可包含英文字母、数字、半角句号（.）、短划线（-）和下划线（\_）。 |
|DisplayName|String|否|alice|RAM用户的显示名称。

 长度为1~128个字符。 |
|MobilePhone|String|否|86-1868888\*\*\*\*|RAM用户的手机号码。

 格式：国际区号-号码。

 **说明：** 该参数仅适用于中国站。 |
|Email|String|否|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|Comments|String|否|This is a cloud computing engineer.|备注。

 长度为1~128个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~28676~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|User|Object| |RAM用户信息。 |
|DisplayName|String|alice|RAM用户的显示名称。 |
|Email|String|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|MobilePhone|String|86-1868888\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UserId|String|122748924538\*\*\*\*|RAM用户的唯一标识。 |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2015-01-23T12:33:18Z|RAM用户的创建时间（UTC时间）。 |
|UserName|String|alice|RAM用户的名称。 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=alice
&DisplayName=alice
&MobilePhone=86-1868888****
&Email=alice@example.com
&Comments=This is a cloud computing engineer.
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<CreateUserResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <User>
        <UserId>122748924538****</UserId>
        <UserName>alice</UserName>
        <DisplayName>alice</DisplayName>
        <MobilePhone>86-1868888****</MobilePhone>
        <Email>alice@example.com</Email>
        <Comments>This is a cloud computing engineer.</Comments>
        <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    </User>
</CreateUserResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "04F0F334-1335-436C-A1D7-6C044FE73368",
  "User" : {
    "UserId" : "122748924538****",
    "UserName" : "alice",
    "DisplayName" : "alice",
    "MobilePhone" : "86-1868888****",
    "Email" : "alice@example.com",
    "Comments" : "This is a cloud computing engineer.",
    "CreateDate" : "2015-01-23T12:33:18Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

成功创建RAM用户后，您可以进行以下的后续操作：

-   调用CreateLoginProfile接口为RAM用户启用Web控制台登录，可以配置登录密码等信息。更多信息，请参见[CreateLoginProfile](~~28685~~)。
-   调用CreateAccessKey接口为RAM用户创建访问密钥。更多信息，请参见[CreateAccessKey](~~28689~~)。

