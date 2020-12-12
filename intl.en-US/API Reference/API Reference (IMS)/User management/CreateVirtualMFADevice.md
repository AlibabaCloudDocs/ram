# CreateVirtualMFADevice

Creates a multi-factor authentication \(MFA\) device.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=CreateVirtualMFADevice&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateVirtualMFADevice|The operation that you want to perform. Set the value to CreateVirtualMFADevice. |
|VirtualMFADeviceName|String|Yes|device001|The name of the MFA device.

 The name must be 1 to 64 characters in length and can contain letters, digits, and hyphens \(-\). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|C609CC97-10FE-43EB-BE32-BDC219D8F1E4|The ID of the request. |
|VirtualMFADevice|Struct| |The information of the MFA device. |
|Base32StringSeed|String|LD3CJ23Z2VGEX6R7ZTQCOA4XL2KODS5PKH7442NLKYX2PVHSHYB7UT3TS5HA\*\*\*\*|The key of the MFA device. |
|QRCodePNG|String|YXNkZmFzZDlmeW5hc2Q5OGZoODd4bXJmcThhaGU5aSBmYXNkZiBzYWRmIGFGIDRxd2VjIGEgdHEz\*\*\*\*|The Base64-encoded QR code of the key. |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/device001|The serial number of the MFA device. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=CreateVirtualMFADevice
&VirtualMFADeviceName=device001
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

