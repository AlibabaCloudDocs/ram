# GetAccountMFAInfo

调用GetAccountMFAInfo查询阿里云账号（主账号）的多因素认证设备信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetAccountMFAInfo&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAccountMFAInfo|要执行的操作。取值：GetAccountMFAInfo。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsMFAEnable|Boolean|false|是否已启用多因素认证设备。取值：

 -   true：已启用。
-   false：未启用。 |
|RequestId|String|4BE83135-0B08-467C-B3A2-27B312FD0F57|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetAccountMFAInfo
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetAccountMFAInfoResponse>
	  <RequestId>4BE83135-0B08-467C-B3A2-27B312FD0F57</RequestId>
	  <IsMFAEnable>false</IsMFAEnable>
</GetAccountMFAInfoResponse>
```

`JSON` 格式

```
{
  "RequestId": "4BE83135-0B08-467C-B3A2-27B312FD0F57",
  "IsMFAEnable": false
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

