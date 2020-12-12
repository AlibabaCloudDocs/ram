# DeleteLoginProfile

调用DeleteLoginProfile关闭指定RAM用户的控制台登录。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=DeleteLoginProfile&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLoginProfile|要执行的操作。取值：DeleteLoginProfile。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=DeleteLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteLoginProfileResponse>
            <RequestId>B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC</RequestId>
</DeleteLoginProfileResponse>
```

`JSON` 格式

```
{
  "RequestId": "B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

