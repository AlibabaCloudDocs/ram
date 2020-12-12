# BindMFADevice

Binds a multi-factor authentication \(MFA\) device to a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=BindMFADevice&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|BindMFADevice|The operation that you want to perform. Set the value to BindMFADevice. |
|AuthenticationCode1|String|Yes|123456|The first verification code.

 **Note:** You can call the [CreateVirtualMFADevice](~~186179~~) operation to create an MFA device and generate a key \(value of `Base32StringSeed`\). Then, use the key on the Alibaba Cloud app to manually add an MFA device, and obtain the two consecutive verification codes. |
|AuthenticationCode2|String|Yes|654321|The second verification code.

 **Note:** You can call the [CreateVirtualMFADevice](~~186179~~) operation to create an MFA device and generate a key \(value of `Base32StringSeed`\). Then, use the key on the Alibaba Cloud app to manually add an MFA device, and obtain the two consecutive verification codes. |
|SerialNumber|String|Yes|acs:ram::177242285274\*\*\*\*:mfa/device001|The serial number of the MFA device.

 **Note:** You can call the [CreateVirtualMFADevice](~~186179~~) operation to obtain the serial number of the MFA device. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=BindMFADevice
&AuthenticationCode1=123456
&AuthenticationCode2=654321
&SerialNumber=acs:ram::177242285274****:mfa/device001
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<BindMFADeviceResponse>
            <RequestId>B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC</RequestId>
</BindMFADeviceResponse>
```

`JSON` format

```
{
  "RequestId": "B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

