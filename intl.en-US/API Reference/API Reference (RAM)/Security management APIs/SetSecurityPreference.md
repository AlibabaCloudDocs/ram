# SetSecurityPreference

Sets security preferences.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer automatically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ram&api=SetSecurityPreference&type=RPC&version=2015-05-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetSecurityPreference|The operation that you want to perform. Set the value to SetSecurityPreference. |
|EnableSaveMFATicket|Boolean|No|true|Specifies whether RAM users can save multi-factor authentication \(MFA\) security codes during logon. The security codes are valid for 7 days. Valid values:

 -   true: RAM users can save MFA security codes during logon.
-   false: RAM users cannot save MFA security codes during logon. This is the default value. |
|AllowUserToChangePassword|Boolean|No|true|Specifies whether RAM users can change their passwords. Valid values:

 -   true: RAM users can change their passwords. This is the default value.
-   false: RAM users cannot change their passwords. |
|AllowUserToManageAccessKeys|Boolean|No|false|Specifies whether RAM users can manage their AccessKey pairs. Valid values:

 -   true: RAM users can manage their AccessKey pairs.
-   false: RAM users cannot manage their AccessKey pairs. This is the default value. |
|AllowUserToManagePublicKeys|Boolean|No|false|Specifies whether RAM users can manage their public keys. Valid values:

 -   true: RAM users can manage their public keys.
-   false: RAM users cannot manage their public keys. This is the default value.

 **Note:** This parameter is valid only for the Japan site. |
|AllowUserToManageMFADevices|Boolean|No|true|Specifies whether RAM users can manage their MFA devices. Valid values:

 -   true: RAM users can manage their MFA devices. This is the default value.
-   false: RAM users cannot manage their MFA devices. |
|LoginSessionDuration|Integer|No|6|The validity period of the logon session of the RAM user.

 Valid values: 6 to 24. Default value: 6. Unit: hours. |
|LoginNetworkMasks|String|No|10.0.0.0/8|The subnet mask that specifies the IP addresses from which logon to the console is allowed. This parameter applies to password-based logon and single sign-on \(SSO\). However, this parameter does not apply to API calls that are authenticated based on AccessKey pairs.

 -   If a subnet mask is specified, RAM users can log on to the console only by using the IP addresses in the subnet.
-   If you do not specify a subnet mask, RAM users can log on to the console by using all IP addresses.

 If you want to specify multiple subnet masks, separate the subnet masks with semicolons \(;\). Example: 192.168.0.0/16;10.0.0.0/8.

 A maximum of 25 subnet masks can be set. The total length of the subnet masks can be 1 to 512 characters. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|A978915D-F279-4CA0-A89B-9A71219FFB3E|The ID of the request. |
|SecurityPreference|Struct| |The security preferences. |
|AccessKeyPreference|Struct| |The AccessKey pair preference. |
|AllowUserToManageAccessKeys|Boolean|false|Indicates whether RAM users can manage their AccessKey pairs. |
|LoginProfilePreference|Struct| |The logon preference. |
|AllowUserToChangePassword|Boolean|true|Indicates whether RAM users can change their passwords. |
|EnableSaveMFATicket|Boolean|false|Indicates whether RAM users can save MFA security codes during logon. |
|LoginNetworkMasks|String|10.0.0.0/8|The subnet masks. |
|LoginSessionDuration|Integer|6|The validity period of the logon session of the RAM user. |
|MFAPreference|Struct| |The MFA preference. |
|AllowUserToManageMFADevices|Boolean|false|Indicates whether RAM users can manage their MFA devices. |
|PublicKeyPreference|Struct| |The public key preference.

 **Note:** This parameter is valid only for the Japan site. |
|AllowUserToManagePublicKeys|Boolean|false|Indicates whether RAM users can manage their public keys. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=SetSecurityPreference
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetSecurityPreferenceResponse>
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
		    <PublicKeyPreference>
			      <AllowUserToManagePublicKeys>false</AllowUserToManagePublicKeys>
		    </PublicKeyPreference>
		    <MFAPreference>
			      <AllowUserToManageMFADevices>true</AllowUserToManageMFADevices>
		    </MFAPreference>
	  </SecurityPreference>
	  <RequestId>A978915D-F279-4CA0-A89B-9A71219FFB3E</RequestId>
</SetSecurityPreferenceResponse>
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
		"PublicKeyPreference": {
			"AllowUserToManagePublicKeys": false
		},
		"MFAPreference": {
			"AllowUserToManageMFADevices": true
		}
	},
	"RequestId": "A978915D-F279-4CA0-A89B-9A71219FFB3E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram).

