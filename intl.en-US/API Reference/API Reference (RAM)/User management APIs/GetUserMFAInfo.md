# GetUserMFAInfo

Queries the multi-factor authentication \(MFA\) device that is attached to a Resource Access Management \(RAM\) user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ram&api=GetUserMFAInfo&type=RPC&version=2015-05-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetUserMFAInfo|The operation that you want to perform. Set the value to GetUserMFAInfo. |
|UserName|String|Yes|test|The username of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MFADevice|Struct| |The information about the MFA device that is attached to the RAM user. |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/test|The serial number of the MFA device. |
|Type|String|VMFA|The type of the MFA device. Valid values:

 -   VMFA: virtual MFA device
-   U2F: Universal 2nd Factor \(U2F\) security key |
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=GetUserMFAInfo
&UserName=test
&<Common Request Parameters>
```

Sample success responses

`XML` format

```
<GetUserMFAInfoResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
	  <MFADevice>
		    <SerialNumber>acs:ram::177242285274****:mfa/test</SerialNumber>
		    <Type>VMFA</Type>
	  </MFADevice>
</GetUserMFAInfoResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "MFADevice": {
        "SerialNumber":"acs:ram::177242285274****:mfa/test",
        "Type": "VMFA"
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram).

