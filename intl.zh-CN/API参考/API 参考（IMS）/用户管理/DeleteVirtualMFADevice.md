# DeleteVirtualMFADevice

调用DeleteVirtualMFADevice删除多因素认证设备。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=DeleteVirtualMFADevice&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVirtualMFADevice|要执行的操作。取值：DeleteVirtualMFADevice。 |
|SerialNumber|String|是|acs:ram::123456789012\*\*\*\*:mfa/device002|设备序列号。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=DeleteVirtualMFADevice
&SerialNumber=acs:ram::123456789012****:mfa/device002
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteVirtualMFADeviceResponse>
            <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteVirtualMFADeviceResponse>
```

`JSON` 格式

```
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

