# UpdateLoginProfile

Modifies the logon information of a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=UpdateLoginProfile&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateLoginProfile|The operation that you want to perform. Set the value to UpdateLoginProfile. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |
|Password|String|No|mypassword|The new password that is used to log on to the console.

The password must meet the complexity requirements. |
|PasswordResetRequired|Boolean|No|false|Specifies whether the RAM user must reset the password at the next logon. Valid values:

-   true
-   false |
|MFABindRequired|Boolean|No|false|Specifies whether multi-factor authentication \(MFA\) must be enabled. Valid values:

-   true. The value true indicates that the RAM user must bind an MFA device at the next logon.
-   false. |
|Status|String|No|Active|The status of password-based logon. Valid values:

-   Active
-   Inactive |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoginProfile|Struct| |The logon information. |
|MFABindRequired|Boolean|false|Indicates whether MFA must be enabled. |
|PasswordResetRequired|Boolean|false|Indicates whether the RAM user must reset the password at the next logon. |
|Status|String|Active|The status of password-based logon. |
|UpdateDate|String|2020-10-14T07:48:41Z|The update time. |
|UserPrincipalName|String|test@example11.onaliyun.com|The logon name of the RAM user. |
|RequestId|String|BCDB6A7F-2199-41D9-B577-4FA536A5ADE1|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=UpdateLoginProfile
&UserPrincipalName=test@example.onaliyun.com
&Password=mypassword
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UpdateLoginProfileResponse>
      <RequestId>BCDB6A7F-2199-41D9-B577-4FA536A5ADE1</RequestId>
      <LoginProfile>
            <Status>Active</Status>
            <UpdateDate>2020-10-14T07:48:41Z</UpdateDate>
            <PasswordResetRequired>false</PasswordResetRequired>
            <UserPrincipalName>test@example11.onaliyun.com</UserPrincipalName>
            <MFABindRequired>false</MFABindRequired>
      </LoginProfile>
</UpdateLoginProfileResponse>
```

`JSON` format

```
{
  "RequestId": "BCDB6A7F-2199-41D9-B577-4FA536A5ADE1",
  "LoginProfile": {
    "Status": "Active",
    "UpdateDate": "2020-10-14T07:48:41Z",
    "PasswordResetRequired": false,
    "UserPrincipalName": "test@example11.onaliyun.com",
    "MFABindRequired": false
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

