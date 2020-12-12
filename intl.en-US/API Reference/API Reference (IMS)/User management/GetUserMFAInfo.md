# GetUserMFAInfo

Queries the information of the multi-factor authentication \(MFA\) device that is bound to a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetUserMFAInfo&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetUserMFAInfo|The operation that you want to perform. Set the value to GetUserMFAInfo. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user. This parameter is differently set in the following scenarios:

 -   If you use a RAM user to call this operation, this parameter can be left empty. If you do not set this parameter, the information of the MFA device that is bound to the current RAM user is queried.
-   If you use an Alibaba Cloud account to call this operation, you must set this parameter to the logon name of the RAM user that you want to query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsMFAEnable|Boolean|true|Indicates whether MFA is enabled. Valid values:

 -   true
-   false |
|MFADevice|Struct| |The information of the MFA device. |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/device001|The serial number of the MFA device. |
|RequestId|String|FCF7322A-20A9-4F68-8B7F-F86958839BC0|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetUserMFAInfo
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetUserMFAInfoResponse>
	  <MFADevice>
		    <SerialNumber>acs:ram::177242285274****:mfa/device001</SerialNumber>
	  </MFADevice>
	  <RequestId>FCF7322A-20A9-4F68-8B7F-F86958839BC0</RequestId>
	  <IsMFAEnable>true</IsMFAEnable>
</GetUserMFAInfoResponse>
```

`JSON` format

```
{
  "MFADevice": {
    "SerialNumber": "acs:ram::177242285274****:mfa/device001"
  },
  "RequestId": "FCF7322A-20A9-4F68-8B7F-F86958839BC0",
  "IsMFAEnable": true
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

