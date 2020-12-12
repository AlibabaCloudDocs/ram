# GetSecurityPreference

Queries the security preferences for RAM users.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetSecurityPreference&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetSecurityPreference|The operation that you want to perform. Set the value to GetSecurityPreference. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|30C9068D-FBAA-4998-9986-8A562FED0BC3|The ID of the request. |
|SecurityPreference|Struct| |The details of security preferences. |
|AccessKeyPreference|Struct| |The AccessKey pair preference. |
|AllowUserToManageAccessKeys|Boolean|false|Indicates whether RAM users can manage their AccessKey pairs. |
|LoginProfilePreference|Struct| |The logon preference. |
|AllowUserToChangePassword|Boolean|true|Indicates whether RAM users can change their passwords. |
|EnableSaveMFATicket|Boolean|false|Indicates whether RAM users can save the multi-factor authentication \(MFA\) status during logon. If this parameter is true, MFA is not required within seven days. |
|LoginNetworkMasks|String|10.0.0.0/8|The subnet mask. |
|LoginSessionDuration|Integer|6|The validity period of the logon session of the RAM user. |
|MFAPreference|Struct| |The MFA preference. |
|AllowUserToManageMFADevices|Boolean|false|Indicates whether RAM users can manage their MFA devices. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetSecurityPreference
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetSecurityPreferenceResponse>
	  <SecurityPreference>
		    <LoginProfilePreference>
			      <LoginSessionDuration>6</LoginSessionDuration>
			      <LoginNetworkMasks></LoginNetworkMasks>
			      <AllowUserToChangePassword>true</AllowUserToChangePassword>
			      <EnableSaveMFATicket>false</EnableSaveMFATicket>
		    </LoginProfilePreference>
		    <AccessKeyPreference>
			      <AllowUserToManageAccessKeys>false</AllowUserToManageAccessKeys>
		    </AccessKeyPreference>
		    <MFAPreference>
			      <AllowUserToManageMFADevices>true</AllowUserToManageMFADevices>
		    </MFAPreference>
	  </SecurityPreference>
	  <RequestId>30C9068D-FBAA-4998-9986-8A562FED0BC3</RequestId>
</GetSecurityPreferenceResponse>
```

`JSON` format

```
{
  "SecurityPreference": {
    "LoginProfilePreference": {
      "LoginSessionDuration": 6,
      "LoginNetworkMasks": "",
      "AllowUserToChangePassword": true,
      "EnableSaveMFATicket": false
    },
    "AccessKeyPreference": {
      "AllowUserToManageAccessKeys": false
    },
    "MFAPreference": {
      "AllowUserToManageMFADevices": true
    }
  },
  "RequestId": "30C9068D-FBAA-4998-9986-8A562FED0BC3"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

