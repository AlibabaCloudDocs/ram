# RemoveUserFromGroup

调用RemoveUserFromGroup将RAM用户从用户组中移除。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=RemoveUserFromGroup&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveUserFromGroup|要执行的操作。取值：RemoveUserFromGroup。 |
|GroupName|String|是|Test-Team|用户组名称。 |
|UserPrincipalName|String|是|alice@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=RemoveUserFromGroup
&GroupName=Test-Team
&UserPrincipalName=alice@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<RemoveUserFromGroupResponse>
          <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</RemoveUserFromGroupResponse>
```

`JSON` 格式

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

