# DeleteGroup

调用DeleteGroup删除指定的用户组。

删除用户组前，请确保用户组没有绑定任何权限策略且用户组内没有RAM用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=DeleteGroup&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteGroup|要执行的操作。取值：DeleteGroup。 |
|GroupName|String|是|Dev-Team|用户组名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=DeleteGroup
&GroupName=Dev-Team
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteGroupResponse>
        <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</DeleteGroupResponse>
```

`JSON` 格式

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

