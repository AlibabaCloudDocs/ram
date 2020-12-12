# DeleteUser

调用DeleteUser删除RAM用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=DeleteUser&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteUser|要执行的操作。取值：DeleteUser。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|指定的RAM用户登录名称。

 **说明：** `UserPrincipalName`与`UserId`参数，必须指定一个，但不能同时指定。 |
|UserId|String|否|20732900249392\*\*\*\*|指定的RAM用户ID。

 **说明：** `UserPrincipalName`与`UserId`参数，必须指定一个，但不能同时指定。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=DeleteUser
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteUserResponse>
      <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</DeleteUserResponse>
```

`JSON` 格式

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

