# CreateUser

调用CreateUser接口创建RAM用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=CreateUser&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUser|要执行的操作。取值：CreateUser。 |
|UserName|String|是|zhangq\*\*\*\*|RAM用户名称。

 长度为1~64个字符，可包含英文字母、数字、英文句点（.）、短划线（-）和下划线（\_）。 |
|DisplayName|String|否|zhangq\*\*\*\*|RAM用户显示名称。

 长度为1~128个字符或汉字，可包含英文字母、数字、英文句点（.）、at（@）、短划线（-）和空格。 |
|MobilePhone|String|否|86-1868888\*\*\*\*|RAM用户的手机号。

 格式：国际区号-号码。 |
|Email|String|否|zhangq\*\*\*\*@example.com|RAM用户的邮箱。 |
|Comments|String|否|This is a cloud computing engineer.|备注。

 长度为1~128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |
|User|Struct| |RAM用户信息。 |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。 |
|DisplayName|String|zhangq\*\*\*\*|显示名称。 |
|Email|String|zhangq\*\*\*\*@example.com|RAM用户的邮箱。 |
|MobilePhone|String|86-1868888\*\*\*\*|RAM用户的手机号。 |
|UserId|String|122748924538\*\*\*\*|RAM用户唯一标识。 |
|UserName|String|zhangq\*\*\*\*|RAM用户名称。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangq****
&DisplayName=zhangq****
&MobilePhone=86-1868888****
&Email=zhangq****@example.com
&Comments=This is a cloud computing engineer.
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateUserResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <User>
            <UserId>122748924538****</UserId>
            <UserName>zhangq****</UserName>
            <DisplayName>zhangq****</DisplayName>
            <MobilePhone>86-1868888****</MobilePhone>
            <Email>zhangq****@example.com</Email>
            <Comments>This is a cloud computing engineer.</Comments>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      </User>
</CreateUserResponse>
```

`JSON` 格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "User": {
        "UserId": "122748924538****",
        "UserName": "zhangq****",
        "DisplayName": "zhangq****",
        "MobilePhone": "86-1868888****",
        "Email": "zhangq****@example.com",
        "Comments": "This is a cloud computing engineer.",
        "CreateDate": "2015-01-23T12:33:18Z"
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

成功创建RAM用户后，您可以进行如下的后续操作：

-   调用CreateLoginProfile接口为RAM用户启用Web控制台登录，可以配置登录密码等信息。详情请参见[CreateLoginProfile](~~28685~~)。
-   调用CreateAccessKey接口为RAM用户创建访问密钥。详情请参见[CreateAccessKey](~~28689~~)。

