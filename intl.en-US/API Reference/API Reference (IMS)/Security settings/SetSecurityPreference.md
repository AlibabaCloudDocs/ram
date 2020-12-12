# SetSecurityPreference

Configures the security preferences for RAM users.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=SetSecurityPreference&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetSecurityPreference|The operation that you want to perform. Set the value to SetSecurityPreference. |
|EnableSaveMFATicket|Boolean|No|false|Specifies whether RAM users can save the status of multi-factor authentication \(MFA\) during logon. The status is valid for seven days. Default value: false. Valid values:

 -   true
-   false |
|AllowUserToChangePassword|Boolean|No|true|Specifies whether RAM users can change their passwords. Default value: true. Valid values:

 -   true
-   false |
|AllowUserToManageAccessKeys|Boolean|No|false|Specifies whether RAM users can manage their AccessKey pairs. Default value: false. Valid values:

 -   true
-   false |
|AllowUserToManageMFADevices|Boolean|No|true|Specifies whether RAM users can manage their MFA devices. Default value: true. Valid values:

 -   true
-   false |
|LoginSessionDuration|Integer|No|6|The validity period of the logon session of the RAM user.

 Valid values: 6 to 24. Unit: hours.

 Default value: 6. |
|LoginNetworkMasks|String|No|10.0.0.0/8|The subnet mask that specifies the IP addresses from which logon to the console is allowed. This parameter applies to password-based logon and single sign-on \(SSO\). However, this parameter does not apply to API calls that are authenticated based on AccessKey pairs.

 -   If a subnet mask is specified, RAM users can log on to the console only by using the IP addresses in the subnet.
-   If you do not specify a subnet mask, RAM users can log on to the console by using all IP addresses.

 If you need to specify multiple subnet masks, separate masks with semicolons \(;\). Example: 192.168.0.0/16;10.0.0.0/8. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|17494710-B4BA-4185-BBBB-C1A6ABDE1639|The ID of the request. |
|SecurityPreference|Struct| |The details of security preferences. |
|AccessKeyPreference|Struct| |The AccessKey pair preference. |
|AllowUserToManageAccessKeys|Boolean|false|Indicates whether RAM users can manage their AccessKey pairs. |
|LoginProfilePreference|Struct| |The logon preference. |
|AllowUserToChangePassword|Boolean|true|Indicates whether RAM users can change their passwords. |
|EnableSaveMFATicket|Boolean|false|Indicates whether RAM users can save the MFA status during logon. If this parameter is true, MFA is not required within seven days. |
|LoginNetworkMasks|String|10.0.0.0/8|The subnet mask. |
|LoginSessionDuration|Integer|6|The validity period of the logon session of the RAM user. |
|MFAPreference|Struct| |The MFA preference. |
|AllowUserToManageMFADevices|Boolean|false|Indicates whether RAM users can manage their MFA devices. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=SetSecurityPreference
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
		    <MFAPreference>
			      <AllowUserToManageMFADevices>true</AllowUserToManageMFADevices>
		    </MFAPreference>
	  </SecurityPreference>
	  <RequestId>17494710-B4BA-4185-BBBB-C1A6ABDE1639</RequestId>
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
    "MFAPreference": {
      "AllowUserToManageMFADevices": true
    }
  },
  "RequestId": "17494710-B4BA-4185-BBBB-C1A6ABDE1639"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

