# SetPasswordPolicy

Configures the password policy for RAM users.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=SetPasswordPolicy&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetPasswordPolicy|The operation that you want to perform. Set the value to SetPasswordPolicy. |
|MinimumPasswordLength|Integer|No|8|The minimum number of characters in the password.

 Valid values: 8 to 32. Default value: 8. |
|RequireLowercaseCharacters|Boolean|No|false|Specifies whether the password must contain lowercase letters. Default value: false. Valid values:

 -   true
-   false |
|RequireUppercaseCharacters|Boolean|No|false|Specifies whether the password must contain uppercase letters. Default value: false. Valid values:

 -   true
-   false |
|RequireNumbers|Boolean|No|false|Specifies whether the password must contain digits. Default value: false. Valid values:

 -   true
-   false |
|RequireSymbols|Boolean|No|false|Specifies whether the password must contain special characters. Default value: false. Valid values:

 -   true
-   false |
|HardExpire|Boolean|No|false|Specifies whether to disable logon after the password expires. Valid values:

 -   true: After the password expires, you cannot use the password to log on to the console. You can log on to the console only after you reset the password by using your Alibaba Cloud account or as a RAM user that has administrative rights.
-   false: After the password expires, you can change the password to log on to the console. This is the default value. |
|MaxLoginAttemps|Integer|No|0|The maximum number of password retries. If you enter the wrong passwords for the specified consecutive times, the account is locked for one hour.

 Valid values: 0 to 32.

 The default value is 0, which indicates that the password retries are not limited. |
|PasswordReusePrevention|Integer|No|0|The policy for password history check.

 The previous N passwords cannot be reused. Valid values of N: 0 to 24.

 The default value is 0, which indicates that RAM users can reuse previous passwords. |
|MaxPasswordAge|Integer|No|0|The validity period of the password.

 Valid values: 0 to 1095. Unit: days.

 The default value is 0, which indicates that the password never expires. |
|MinimumPasswordDifferentCharacter|Integer|No|0|The minimum number of unique characters in the password.

 Valid values: 0 to 8.

 The default value is 0, which indicates that no limits are imposed on the number of unique characters in a password. |
|PasswordNotContainUserName|Boolean|No|false|Specifies whether to exclude the username from the password. Valid values:

 -   true: A password cannot contain the username.
-   false: A password can contain the username. This is the default value. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|PasswordPolicy|Struct| |The details of the password policy. |
|HardExpire|Boolean|false|Indicates whether to disable logon after the password expires. |
|MaxLoginAttemps|Integer|0|The maximum number of password retries. |
|MaxPasswordAge|Integer|0|The validity period of the password. |
|MinimumPasswordDifferentCharacter|Integer|0|The minimum number of unique characters in the password. |
|MinimumPasswordLength|Integer|8|The minimum number of characters in the password. |
|PasswordNotContainUserName|Boolean|false|Indicates whether to exclude the username from the password. |
|PasswordReusePrevention|Integer|0|The policy for password history check. |
|RequireLowercaseCharacters|Boolean|false|Indicates whether the password must contain lowercase letters. |
|RequireNumbers|Boolean|false|Indicates whether the password must contain digits. |
|RequireSymbols|Boolean|false|Indicates whether the password must contain special characters. |
|RequireUppercaseCharacters|Boolean|false|Indicates whether the password must contain uppercase letters. |
|RequestId|String|3FB5551F-B2ED-40D4-8392-1E4AC2384EFD|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=SetPasswordPolicy
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetPasswordPolicyResponse>
	  <RequestId>3FB5551F-B2ED-40D4-8392-1E4AC2384EFD</RequestId>
	  <PasswordPolicy>
		    <MinimumPasswordLength>8</MinimumPasswordLength>
		    <RequireLowercaseCharacters>false</RequireLowercaseCharacters>
		    <HardExpire>false</HardExpire>
		    <RequireNumbers>false</RequireNumbers>
		    <MaxLoginAttemps>0</MaxLoginAttemps>
		    <PasswordReusePrevention>0</PasswordReusePrevention>
		    <MaxPasswordAge>0</MaxPasswordAge>
		    <PasswordNotContainUserName>false</PasswordNotContainUserName>
		    <RequireUppercaseCharacters>false</RequireUppercaseCharacters>
		    <MinimumPasswordDifferentCharacter>0</MinimumPasswordDifferentCharacter>
		    <RequireSymbols>false</RequireSymbols>
	  </PasswordPolicy>
</SetPasswordPolicyResponse>
```

`JSON` format

```
{
  "RequestId": "3FB5551F-B2ED-40D4-8392-1E4AC2384EFD",
  "PasswordPolicy": {
    "MinimumPasswordLength": 8,
    "RequireLowercaseCharacters": false,
    "HardExpire": false,
    "RequireNumbers": false,
    "MaxLoginAttemps": 0,
    "PasswordReusePrevention": 0,
    "MaxPasswordAge": 0,
    "PasswordNotContainUserName": false,
    "RequireUppercaseCharacters": false,
    "MinimumPasswordDifferentCharacter": 0,
    "RequireSymbols": false
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

