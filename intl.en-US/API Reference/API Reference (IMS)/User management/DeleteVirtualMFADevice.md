# DeleteVirtualMFADevice

Deletes a multi-factor authentication \(MFA\) device.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=DeleteVirtualMFADevice&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteVirtualMFADevice|The operation that you want to perform. Set the value to DeleteVirtualMFADevice. |
|SerialNumber|String|Yes|acs:ram::123456789012\*\*\*\*:mfa/device002|The serial number of the MFA device. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=DeleteVirtualMFADevice
&SerialNumber=acs:ram::123456789012****:mfa/device002
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteVirtualMFADeviceResponse>
            <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteVirtualMFADeviceResponse>
```

`JSON` format

```
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

