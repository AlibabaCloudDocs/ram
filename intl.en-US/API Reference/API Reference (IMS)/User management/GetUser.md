# GetUser

Queries the information of a RAM user.

This topic provides an example to show how to query the information of a RAM user named `test@example.onaliyun.com`.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetUser&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetUser|The operation that you want to perform. Set the value to GetUser. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 The name is in the format of `<username>@<AccountAlias>.onaliyun.com`. `<username>` is the name of the RAM user. `<AccountAlias>.onaliyun.com` is the default domain name.

 The value of `UserPrincipalName` must be 1 to 128 characters in length and can contain letters, digits, periods \(.\), hyphens \(-\), and underscores \(\_\). The value of `<username>` must be 1 to 64 characters in length.

 **Note:** You must specify only one of the following parameters: `UserPrincipalName`, `UserId`, and `UserAccessKeyId`. |
|UserId|String|No|20732900249392\*\*\*\*|The ID of the RAM user.

 **Note:** You must specify only one of the following parameters: `UserPrincipalName`, `UserId`, and `UserAccessKeyId`. |
|UserAccessKeyId|String|No|LTAI4GFTgcR8m8cZQDTH\*\*\*\*|The AccessKey ID of the RAM user.

 **Note:** You must specify only one of the following parameters: `UserPrincipalName`, `UserId`, and `UserAccessKeyId`. |

For more information about common parameters, see [Common parameters](~~187377~~).

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|4507D1CD-526A-4E2B-A1E2-3AB045D1EE0B|The ID of the request. |
|User|Struct| |The information of the RAM user. |
|Comments|String|This is a cloud computing engineer.|The description of the RAM user. |
|CreateDate|String|2020-10-12T09:12:00Z|The time when the RAM user was created. |
|DisplayName|String|test|The display name of the RAM user. |
|Email|String|alice@example.com|The email address of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|LastLoginDate|String|2020-10-12T09:12:00Z|The last time when the RAM user logged on to the console. |
|MobilePhone|String|86-1868888\*\*\*\*|The mobile phone number of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|UpdateDate|String|2020-10-13T07:39:22Z|The time when the information of the RAM user was updated. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetUser
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetUserResponse>
	  <User>
		    <UpdateDate>2020-10-13T07:39:22Z</UpdateDate>
		    <Email>alice@example.com</Email>
		    <Comments>This is a cloud computing engineer.</Comments>
		    <UserId>20732900249392****</UserId>
		    <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
		    <DisplayName>test</DisplayName>
		    <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    <CreateDate>2020-10-12T09:12:00Z</CreateDate>
		    <MobilePhone>86-1868888****</MobilePhone>
	  </User>
	  <RequestId>4507D1CD-526A-4E2B-A1E2-3AB045D1EE0B</RequestId>
</GetUserResponse>
```

`JSON` format

```
{
  "User": {
    "UpdateDate": "2020-10-13T07:39:22Z",
    "Email": "alice@example.com",
    "Comments": "This is a cloud computing engineer.",
    "UserId": "20732900249392****",
    "LastLoginDate": "2020-10-12T09:12:00Z",
    "DisplayName": "test",
    "UserPrincipalName": "test@example.onaliyun.com",
    "CreateDate": "2020-10-12T09:12:00Z",
    "MobilePhone": "86-1868888****"
  },
  "RequestId": "4507D1CD-526A-4E2B-A1E2-3AB045D1EE0B"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

