# CreateLoginProfile

Enables logon to the console for a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=CreateLoginProfile&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoginProfile|The operation that you want to perform. Set the value to CreateLoginProfile. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |
|Password|String|Yes|mypassword|The password that is used to log on to the console.

 The password must meet the complexity requirements. |
|PasswordResetRequired|Boolean|No|false|Specifies whether the RAM user must reset the password at the next logon. Default value: false. Valid values:

 -   true
-   false |
|MFABindRequired|Boolean|No|false|Specifies whether multi-factor authentication \(MFA\) must be enabled. Valid values:

 -   true: MFA must be enabled. The RAM user must bind an MFA device at the next logon.
-   false: MFA is not enabled. This is the default value. |
|Status|String|No|Active|The status of password-based logon. Valid values:

 -   Active: Password-based logon is enabled. This is the default value.
-   Inactive: Password-based logon is disabled. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoginProfile|Struct| |The logon information. |
|MFABindRequired|Boolean|false|Indicates whether MFA must be enabled. |
|PasswordResetRequired|Boolean|false|Indicates whether the RAM user must reset the password at the next logon. |
|Status|String|Active|The status of password-based logon. |
|UpdateDate|String|2020-10-14T03:47:51Z|The update time. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |
|RequestId|String|29CB303C-1F05-43A6-A6BC-EBC5A797F8DB|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=CreateLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&Password=mypassword
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoginProfileResponse>
	  <RequestId>29CB303C-1F05-43A6-A6BC-EBC5A797F8DB</RequestId>
	  <LoginProfile>
		    <Status>Active</Status>
		    <UpdateDate>2020-10-14T03:47:51Z</UpdateDate>
		    <PasswordResetRequired>false</PasswordResetRequired>
		    <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    <MFABindRequired>false</MFABindRequired>
	  </LoginProfile>
</CreateLoginProfileResponse>
```

`JSON` format

```
{
  "RequestId": "29CB303C-1F05-43A6-A6BC-EBC5A797F8DB",
  "LoginProfile": {
    "Status": "Active",
    "UpdateDate": "2020-10-14T03:47:51Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

