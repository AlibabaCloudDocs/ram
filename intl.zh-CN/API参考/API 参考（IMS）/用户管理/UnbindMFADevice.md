# UnbindMFADevice

调用UnbindMFADevice为RAM用户解绑多因素认证设备。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=UnbindMFADevice&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UnbindMFADevice|要执行的操作。取值：UnbindMFADevice。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MFADevice|Struct| |多因素认证设备信息。 |
|SerialNumber|String|acs:ram::151298381312\*\*\*\*:mfa/device001|设备序列号。 |
|RequestId|String|A26CB3E9-1021-452A-AC57-3134B3BA0E4C|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=UnbindMFADevice
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UnbindMFADeviceResponse>
	  <MFADevice>
		    <SerialNumber>acs:ram::151298381312****:mfa/device001</SerialNumber>
	  </MFADevice>
	  <RequestId>A26CB3E9-1021-452A-AC57-3134B3BA0E4C</RequestId>
</UnbindMFADeviceResponse>
```

`JSON` 格式

```
{
  "MFADevice": {
    "SerialNumber": "acs:ram::151298381312****:mfa/device001"
  },
  "RequestId": "A26CB3E9-1021-452A-AC57-3134B3BA0E4C"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

