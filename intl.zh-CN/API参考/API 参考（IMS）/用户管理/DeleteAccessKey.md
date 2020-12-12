# DeleteAccessKey

调用DeleteAccessKey删除阿里云账号（主账号）或RAM用户的访问密钥。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=DeleteAccessKey&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteAccessKey|要执行的操作。取值：DeleteAccessKey。 |
|UserAccessKeyId|String|是|LTAI4GFTgcR8m8cZQDTH\*\*\*\*|需要删除的访问密钥ID。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|RAM用户的登录名称。

 如果为空，默认删除当前用户的访问密钥。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=DeleteAccessKey
&UserAccessKeyId=LTAI4GFTgcR8m8cZQDTH****
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteAccessKeyResponse>
          <RequestId>B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC</RequestId>
</DeleteAccessKeyResponse>
```

`JSON` 格式

```
{
  "RequestId": "B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

