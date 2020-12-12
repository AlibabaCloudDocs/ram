# GetDefaultDomain

调用GetDefaultDomain查询默认域名。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetDefaultDomain&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetDefaultDomain|要执行的操作。取值：GetDefaultDomain。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DefaultDomainName|String|examplecompany.onaliyun.com|默认域名。 |
|RequestId|String|66815255-7CCE-4759-AC37-9755794C3626|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetDefaultDomain
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetDefaultDomainResponse>
        <DefaultDomainName>examplecompany.onaliyun.com</DefaultDomainName>
        <RequestId>66815255-7CCE-4759-AC37-9755794C3626</RequestId>
</GetDefaultDomainResponse>
```

`JSON` 格式

```
{
  "DefaultDomainName": "examplecompany.onaliyun.com",
  "RequestId": "66815255-7CCE-4759-AC37-9755794C3626"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

