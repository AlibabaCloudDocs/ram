# GetUserMFAInfo

调用GetUserMFAInfo查询RAM用户绑定的多因素认证设备信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetUserMFAInfo&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetUserMFAInfo|要执行的操作。取值：GetUserMFAInfo。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|RAM用户的登录名称。存在以下两种情况：

 -   当RAM用户调用时，该参数可以为空，为空时默认查询当前RAM用户的多因素认证设备信息。
-   当阿里云账号（主账号）调用时，该参数不能为空，必须指定需要查询的RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsMFAEnable|Boolean|true|是否已启用多因素认证设备。取值：

 -   true：已启用。
-   false：未启用。 |
|MFADevice|Struct| |多因素认证设备信息。 |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/device001|设备序列号。 |
|RequestId|String|FCF7322A-20A9-4F68-8B7F-F86958839BC0|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetUserMFAInfo
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetUserMFAInfoResponse>
	  <MFADevice>
		    <SerialNumber>acs:ram::177242285274****:mfa/device001</SerialNumber>
	  </MFADevice>
	  <RequestId>FCF7322A-20A9-4F68-8B7F-F86958839BC0</RequestId>
	  <IsMFAEnable>true</IsMFAEnable>
</GetUserMFAInfoResponse>
```

`JSON` 格式

```
{
  "MFADevice": {
    "SerialNumber": "acs:ram::177242285274****:mfa/device001"
  },
  "RequestId": "FCF7322A-20A9-4F68-8B7F-F86958839BC0",
  "IsMFAEnable": true
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

