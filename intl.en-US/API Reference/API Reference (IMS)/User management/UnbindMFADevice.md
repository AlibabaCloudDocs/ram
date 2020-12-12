# UnbindMFADevice

Unbinds a multi-factor authentication \(MFA\) device from a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=UnbindMFADevice&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UnbindMFADevice|The operation that you want to perform. Set the value to UnbindMFADevice. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MFADevice|Struct| |The information of the MFA device. |
|SerialNumber|String|acs:ram::151298381312\*\*\*\*:mfa/device001|The serial number of the MFA device. |
|RequestId|String|A26CB3E9-1021-452A-AC57-3134B3BA0E4C|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=UnbindMFADevice
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UnbindMFADeviceResponse>
	  <MFADevice>
		    <SerialNumber>acs:ram::151298381312****:mfa/device001</SerialNumber>
	  </MFADevice>
	  <RequestId>A26CB3E9-1021-452A-AC57-3134B3BA0E4C</RequestId>
</UnbindMFADeviceResponse>
```

`JSON` format

```
{
  "MFADevice": {
    "SerialNumber": "acs:ram::151298381312****:mfa/device001"
  },
  "RequestId": "A26CB3E9-1021-452A-AC57-3134B3BA0E4C"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

