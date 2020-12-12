# GetLoginProfile

Queries the logon information of a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetLoginProfile&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetLoginProfile|The operation that you want to perform. Set the value to GetLoginProfile. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoginProfile|Struct| |The logon information. |
|LastLoginTime|String|2020-10-14T07:25:25Z|The last time when the RAM user logged on to the console. |
|MFABindRequired|Boolean|false|Indicates whether multi-factor authentication \(MFA\) must be enabled. |
|PasswordResetRequired|Boolean|false|Indicates whether the RAM user must reset the password at the next logon. |
|Status|String|Active|The status of password-based logon. |
|UpdateDate|String|2020-10-14T06:56:45Z|The update time. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |
|RequestId|String|E517F18B-632C-48FC-93F1-CDCBCC6F8444|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetLoginProfileResponse>
	  <RequestId>E517F18B-632C-48FC-93F1-CDCBCC6F8444</RequestId>
	  <LoginProfile>
		    <Status>Active</Status>
		    <LastLoginTime>2020-10-14T07:25:25Z</LastLoginTime>
		    <UpdateDate>2020-10-14T07:25:00Z</UpdateDate>
		    <PasswordResetRequired>false</PasswordResetRequired>
		    <UserPrincipalName>test@example11.onaliyun.com</UserPrincipalName>
		    <MFABindRequired>false</MFABindRequired>
	  </LoginProfile>
</GetLoginProfileResponse>
```

`JSON` format

```
{
  "RequestId": "E517F18B-632C-48FC-93F1-CDCBCC6F8444",
  "LoginProfile": {
    "Status": "Active",
    "LastLoginTime": "2020-10-14T07:25:25Z",
    "UpdateDate": "2020-10-14T07:25:00Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example11.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

