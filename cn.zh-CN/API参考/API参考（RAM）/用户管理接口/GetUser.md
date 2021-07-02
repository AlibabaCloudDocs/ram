# GetUser

调用GetUser接口查询RAM用户的详细信息。

本文将提供一个示例，查询RAM用户`alice`的详细信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=GetUser&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetUser|要执行的操作。取值：**GetUser**。 |
|UserName|String|是|alice|RAM用户的名称。

 长度为1~64个字符，可包含英文字母、数字、半角句号（.）、短划线（-）和下划线（\_）。 |

关于公共请求参数的详情，请参见[公共参数](~~28676~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|User|Object| |RAM用户信息。 |
|DisplayName|String|alice|显示名称。 |
|Email|String|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|UpdateDate|String|2015-02-11T03:15:21Z|RAM用户的更新时间（UTC时间）。 |
|MobilePhone|String|86-1860000\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UserId|String|222748924538\*\*\*\*|RAM用户的唯一标识。 |
|Comments|String|这是一位云计算工程师|备注。 |
|LastLoginDate|String|2015-01-23T12:33:18Z|上次使用密码登录时间（UTC时间）。 |
|CreateDate|String|2015-01-23T12:33:18Z|RAM用户的创建时间（UTC时间）。 |
|UserName|String|alice|RAM用户的名称。 |
|RequestId|String|2D69A58F-345C-4FDE-88E4-BF5189484043|请求ID。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=GetUser
&UserName=alice
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetUserResponse>
    <RequestId>2D69A58F-345C-4FDE-88E4-BF5189484043</RequestId>
    <User>
        <UserId>222748924538****</UserId>
        <UserName>alice</UserName>
        <DisplayName>alice</DisplayName>
        <MobilePhone>86-1860000****</MobilePhone>
        <Email>alice@example.com</Email>
        <Comments>This is a cloud computing engineer.</Comments>
        <CreateDate>2015-01-23T12:33:18Z</CreateDate>
        <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
        <LastLoginDate>2015-01-23T12:33:18Z</LastLoginDate>
    </User>
</GetUserResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "2D69A58F-345C-4FDE-88E4-BF5189484043",
  "User" : {
    "UserId" : "222748924538****",
    "UserName" : "alice",
    "DisplayName" : "alice",
    "MobilePhone" : "86-1860000****",
    "Email" : "alice@example.com",
    "Comments" : "This is a cloud computing engineer.",
    "CreateDate" : "2015-01-23T12:33:18Z",
    "UpdateDate" : "2015-02-11T03:15:21Z",
    "LastLoginDate" : "2015-01-23T12:33:18Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

