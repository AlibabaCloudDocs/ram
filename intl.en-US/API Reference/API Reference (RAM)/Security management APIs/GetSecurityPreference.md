# GetSecurityPreference

Queries the security preferences.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ram&api=GetSecurityPreference&type=RPC&version=2015-05-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Required|GetSecurityPreference|The operation that you want to perform. Set the value to GetSecurityPreference. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|DC1213F1-A9D5-4A01-A996-44983689126C|The ID of the request. |
|SecurityPreference|Struct| |The security preferences. |
|AccessKeyPreference|Struct| |The AccessKey pair preference. |
|AllowUserToManageAccessKeys|Boolean|false|Indicates whether RAM users can manage their AccessKey pairs. Valid values:

-   true: RAM users can manage their AccessKey pairs.
-   false: RAM users cannot manage their AccessKey pairs. |
|LoginProfilePreference|Struct| |The logon preferences. |
|AllowUserToChangePassword|Boolean|true|Indicates whether RAM users can change their passwords. Valid values:

-   true: RAM users can change their passwords.
-   false: RAM users cannot change their passwords. |
|EnableSaveMFATicket|Boolean|false|Indicates whether RAM users can save security codes for multi-factor authentication \(MFA\) during logon. Each security code is valid for seven days. Valid values:

-   true: RAM users can save MFA security codes during logon.
-   false: RAM users cannot save MFA security codes during logon. |
|LoginNetworkMasks|String|10.0.0.0/8|The subnet mask that indicates the IP addresses from which logon to the Alibaba Cloud Management Console is allowed. This parameter applies to password-based logon and single sign-on \(SSO\). However, this parameter does not apply to API calls that are authenticated based on AccessKey pairs.

-   If a subnet mask is specified, RAM users can log on to the Alibaba Cloud Management Console only by using the IP addresses in the subnetwork.
-   If no subnet mask is specified, RAM users can log on to the Alibaba Cloud Management Console by using all IP addresses.

If more than one subnet mask is specified, the masks are separated with semicolons \(;\), for example, 192.168.0.0/16;10.0.0.0/8. |
|LoginSessionDuration|Integer|6|The validity period of a logon session of a RAM user. Unit: hours. |
|MFAPreference|Struct| |The MFA preference. |
|AllowUserToManageMFADevices|Boolean|true|Indicates whether RAM users can manage their MFA devices. Valid values:

-   true: RAM users can manage their MFA devices.
-   false: RAM users cannot manage their MFA devices. |
|PublicKeyPreference|Struct| |The public key preference.

**Note:** The public key preference is valid only for the Japan site. |
|AllowUserToManagePublicKeys|Boolean|false|Indicates whether RAM users can manage their public keys. Valid values:

-   true: RAM users can manage their public keys.
-   false: RAM users cannot manage their public keys. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=GetSecurityPreference
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
            <PublicKeyPreference>
                  <AllowUserToManagePublicKeys>false</AllowUserToManagePublicKeys>
            </PublicKeyPreference>
            <MFAPreference>
                  <AllowUserToManageMFADevices>true</AllowUserToManageMFADevices>
            </MFAPreference>
      </SecurityPreference>
      <RequestId>DC1213F1-A9D5-4A01-A996-44983689126C</RequestId>
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
        "PublicKeyPreference": {
            "AllowUserToManagePublicKeys": false
        },
        "MFAPreference": {
            "AllowUserToManageMFADevices": true
        }
    },
    "RequestId": "DC1213F1-A9D5-4A01-A996-44983689126C"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram).

