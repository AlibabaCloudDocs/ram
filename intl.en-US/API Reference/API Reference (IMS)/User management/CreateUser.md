# CreateUser

Creates a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=CreateUser&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateUser|The operation that you want to perform. Set the value to CreateUser. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user.

 The name is in the format of `<username>@<AccountAlias>.onaliyun.com`. `<username>` indicates the name of the RAM user. `<AccountAlias>.onaliyun.com` indicates the default domain name.

 The value of `UserPrincipalName` must be 1 to 128 characters in length. The value of `<username>` must be 1 to 64 characters in length. The name can contain letters, digits, periods \(.\), at signs \(@\), hyphens \(-\), and underscores \(\_\). |
|DisplayName|String|Yes|test|The display name of the RAM user.

 The name must be 1 to 24 characters in length. |
|MobilePhone|String|No|86-1868888\*\*\*\*|The mobile phone number of the RAM user.

 Format: Country calling code-Mobile phone number.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|Email|String|No|alice@example.com|The email address of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|Comments|String|No|This is a cloud computing engineer.|The description.

 The value must be 1 to 128 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|2BB8C44A-2862-4922-AD43-03924749173B|The ID of the request. |
|User|Struct| |The information of the RAM user. |
|Comments|String|This is a cloud computing engineer.|The description. |
|CreateDate|String|2020-10-12T09:12:00Z|The time when the RAM user was created. |
|DisplayName|String|test|The display name of the RAM user. |
|Email|String|alice@example.com|The email address of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|LastLoginDate|String|2020-10-12T09:12:00Z|The last time when the RAM user logged on to the console. |
|MobilePhone|String|86-1868888\*\*\*\*|The mobile phone number of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|UpdateDate|String|2020-10-12T09:12:00Z|The time when the information of the RAM user was updated. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=CreateUser
&UserPrincipalName=test@example.onaliyun.com
&DisplayName=test
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateUserResponse>
	  <User>
		    <UpdateDate>2020-10-12T09:12:00Z</UpdateDate>
		    <Email>alice@example.com</Email>
		    <Comments>This is a cloud computing engineer. </Comments>
		    <UserId>20732900249392****</UserId>
		    <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
		    <DisplayName>test</DisplayName>
		    <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    <CreateDate>2020-10-12T09:12:00Z</CreateDate>
		    <MobilePhone>86-1868888****</MobilePhone>
	  </User>
	  <RequestId>2BB8C44A-2862-4922-AD43-03924749173B</RequestId>
</CreateUserResponse>
```

`JSON` format

```
{
  "User": {
    "UpdateDate": "2020-10-12T09:12:00Z",
    "Email": "alice@example.com",
    "Comments": "This is a cloud computing engineer.",
    "UserId": "20732900249392****",
    "LastLoginDate": "2020-10-12T09:12:00Z",
    "DisplayName": "test",
    "UserPrincipalName": "test@example.onaliyun.com",
    "CreateDate": "2020-10-12T09:12:00Z",
    "MobilePhone": "86-1868888****"
  },
  "RequestId": "2BB8C44A-2862-4922-AD43-03924749173B"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

