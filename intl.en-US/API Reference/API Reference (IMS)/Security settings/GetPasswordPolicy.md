# GetPasswordPolicy

Queries the password policy of RAM users.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetPasswordPolicy&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetPasswordPolicy|The operation that you want to perform. Set the value to GetPasswordPolicy. |

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
|RequestId|String|BDAA8408-E67C-428B-BFF0-1B2AC05C9610|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetPasswordPolicy
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetPasswordPolicyResponse>
      <RequestId>BDAA8408-E67C-428B-BFF0-1B2AC05C9610</RequestId>
      <PasswordPolicy>
            <MinimumPasswordLength>8</MinimumPasswordLength>
            <HardExpire>false</HardExpire>
            <RequireLowercaseCharacters>false</RequireLowercaseCharacters>
            <RequireNumbers>false</RequireNumbers>
            <MaxPasswordAge>0</MaxPasswordAge>
            <MaxLoginAttemps>0</MaxLoginAttemps>
            <PasswordReusePrevention>0</PasswordReusePrevention>
            <PasswordNotContainUserName>false</PasswordNotContainUserName>
            <RequireUppercaseCharacters>false</RequireUppercaseCharacters>
            <MinimumPasswordDifferentCharacter>0</MinimumPasswordDifferentCharacter>
            <RequireSymbols>false</RequireSymbols>
      </PasswordPolicy>
</GetPasswordPolicyResponse>
```

`JSON` format

```
{
  "RequestId": "BDAA8408-E67C-428B-BFF0-1B2AC05C9610",
  "PasswordPolicy": {
    "MinimumPasswordLength": 8,
    "HardExpire": false,
    "RequireLowercaseCharacters": false,
    "RequireNumbers": false,
    "MaxPasswordAge": 0,
    "MaxLoginAttemps": 0,
    "PasswordReusePrevention": 0,
    "PasswordNotContainUserName": false,
    "RequireUppercaseCharacters": false,
    "MinimumPasswordDifferentCharacter": 0,
    "RequireSymbols": false
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

