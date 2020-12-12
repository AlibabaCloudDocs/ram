# CreateVirtualMFADevice

调用CreateVirtualMFADevice创建多因素认证设备。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateVirtualMFADevice&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVirtualMFADevice|要执行的操作。取值：CreateVirtualMFADevice。 |
|VirtualMFADeviceName|String|是|device001|多因素认证设备名称。

 长度为1~64个字符，可包含英文字母、数字和短划线（-）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C609CC97-10FE-43EB-BE32-BDC219D8F1E4|请求ID。 |
|VirtualMFADevice|Struct| |多因素认证设备信息。 |
|Base32StringSeed|String|LD3CJ23Z2VGEX6R7ZTQCOA4XL2KODS5PKH7442NLKYX2PVHSHYB7UT3TS5HA\*\*\*\*|多因素认证设备密钥。 |
|QRCodePNG|String|YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz\*\*\*\*|密钥的二维码，使用Base64编码。 |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/device001|设备序列号。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateVirtualMFADevice
&VirtualMFADeviceName=device001
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateVirtualMFADeviceResponse>
	  <VirtualMFADevice>
		    <SerialNumber>acs:ram::177242285274****:mfa/device001</SerialNumber>
		    <QRCodePNG>YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz****</QRCodePNG>
		    <Base32StringSeed>LD3CJ23Z2VGEX6R7ZTQCOA4XL2KODS5PKH7442NLKYX2PVHSHYB7UT3TS5HA****</Base32StringSeed>
	  </VirtualMFADevice>
	  <RequestId>C609CC97-10FE-43EB-BE32-BDC219D8F1E4</RequestId>
</CreateVirtualMFADeviceResponse>
```

`JSON` 格式

```
{
  "VirtualMFADevice": {
    "SerialNumber": "acs:ram::177242285274****:mfa/device001",
    "QRCodePNG": "YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz****",
    "Base32StringSeed": "LD3CJ23Z2VGEX6R7ZTQCOA4XL2KODS5PKH7442NLKYX2PVHSHYB7UT3TS5HA****"
  },
  "RequestId": "C609CC97-10FE-43EB-BE32-BDC219D8F1E4"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

