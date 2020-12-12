# BindMFADevice

调用BindMFADevice为RAM用户绑定多因素认证设备。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=BindMFADevice&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|BindMFADevice|要执行的操作。取值：BindMFADevice。 |
|AuthenticationCode1|String|是|123456|第一组安全验证码。

 **说明：** 您可以调用[CreateVirtualMFADevice](~~186179~~)创建多因素认证设备并生成密钥（`Base32StringSeed`的值），然后使用该密钥在移动端阿里云应用中手动添加多因素认证设备，最后获取连续的两组安全验证码。 |
|AuthenticationCode2|String|是|654321|第二组安全验证码。

 **说明：** 您可以调用[CreateVirtualMFADevice](~~186179~~)创建多因素认证设备并生成密钥（`Base32StringSeed`的值），然后使用该密钥在移动端阿里云应用中手动添加多因素认证设备，最后获取连续的两组安全验证码。 |
|SerialNumber|String|是|acs:ram::177242285274\*\*\*\*:mfa/device001|多因素认证设备的序列号。

 **说明：** 您可以调用[CreateVirtualMFADevice](~~186179~~)获取多因素认证设备的序列号。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=BindMFADevice
&AuthenticationCode1=123456
&AuthenticationCode2=654321
&SerialNumber=acs:ram::177242285274****:mfa/device001
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<BindMFADeviceResponse>
            <RequestId>B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC</RequestId>
</BindMFADeviceResponse>
```

`JSON` 格式

```
{
  "RequestId": "B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

