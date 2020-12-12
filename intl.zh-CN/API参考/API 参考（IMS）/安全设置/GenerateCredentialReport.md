# GenerateCredentialReport

调用GenerateCredentialReport生成用户凭证报告。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GenerateCredentialReport&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GenerateCredentialReport|要执行的操作。取值：GenerateCredentialReport。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|BBCCA90A-A1F0-4B16-B355-692247197805|请求ID。 |
|State|String|STARTED|用户凭证报告的生成状态。取值：

 -   STARTED：用户凭证报告开始生成。
-   INPROGRESS：用户凭证报告生成中。
-   COMPLETED：用户凭证报告已经生成。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GenerateCredentialReport
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GenerateCredentialReportResponse>
	  <RequestId>BBCCA90A-A1F0-4B16-B355-692247197805</RequestId>
	  <State>STARTED</State>
</GenerateCredentialReportResponse>
```

`JSON` 格式

```
{
  "RequestId": "BBCCA90A-A1F0-4B16-B355-692247197805",
  "State": "STARTED"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

