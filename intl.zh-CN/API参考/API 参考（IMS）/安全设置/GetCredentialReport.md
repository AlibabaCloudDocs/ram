# GetCredentialReport

调用GetCredentialReport查询用户凭证报告内容。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetCredentialReport&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetCredentialReport|要执行的操作。取值：GetCredentialReport。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Content|String|OVZWK4RMOVZW\*\*\*\*|用户凭证报告内容。

 采用Base64编码，解码后是CSV格式的用户凭证报告内容。 |
|GeneratedTime|String|2020-10-19T15:06:52Z|用户凭证报告的生成时间。 |
|RequestId|String|7A01826E-7601-44B0-B4DF-2B0C509836DE|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetCredentialReport
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetCredentialReportResponse>
	  <GeneratedTime>2020-10-19T15:06:52Z</GeneratedTime>
	  <RequestId>7A01826E-7601-44B0-B4DF-2B0C509836DE</RequestId>
	  <Content>OVZWK4RMOVZW****</Content>
</GetCredentialReportResponse>
```

`JSON` 格式

```
{
  "GeneratedTime": "2020-10-19T15:06:52Z",
  "RequestId": "7A01826E-7601-44B0-B4DF-2B0C509836DE",
  "Content": "OVZWK4RMOVZW****"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

