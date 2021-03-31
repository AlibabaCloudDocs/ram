# GetUserMFAInfo

调用GetUserMFAInfo接口查询指定RAM用户的多因素认证设备信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=GetUserMFAInfo&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetUserMFAInfo|要执行的操作。取值：GetUserMFAInfo。 |
|UserName|String|是|test|RAM用户名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MFADevice|Struct| |MFA设备信息。 |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/test|设备序列号。 |
|Type|String|VMFA|多因素认证设备类型。取值：

 -   VMFA：虚拟MFA设备。
-   U2F：U2F安全密钥。 |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=GetUserMFAInfo
&UserName=test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<GetUserMFAInfoResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
	  <MFADevice>
		    <SerialNumber>acs:ram::177242285274****:mfa/test</SerialNumber>
		    <Type>VMFA</Type>
	  </MFADevice>
</GetUserMFAInfoResponse>
```

`JSON`格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "MFADevice": {
        "SerialNumber":"acs:ram::177242285274****:mfa/test",
        "Type": "VMFA"
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

