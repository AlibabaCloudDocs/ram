# ListUsers

Queries the details of all RAM users.

You can call the following API operations to query the information of all RAM users:

-   ListUsers: queries the details of all RAM users.
-   ListUserBasicInfos: queries the basic information of all RAM users. The basic information includes only the logon names \(`UserPrincipalName`\), display names \(`DisplayName`\), and user IDs \( `UserId`\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListUsers&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListUsers|The operation that you want to perform. Set the value to ListUsers. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|1000|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be true.

 Valid values: 1 to 1000. Default value: 1000. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

 -   true
-   false |
|Marker|String|EXAMPLE|The parameter that is used to obtain the truncated part. It takes effect only when `IsTruncated` is set to `true`. |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|The ID of the request. |
|Users|Array of User| |The information of the RAM user. |
|User| | | |
|Comments|String|This is a cloud computing engineer.|The description. |
|CreateDate|String|2020-10-12T09:12:00Z|The time when the RAM user was created. |
|DisplayName|String|test|The display name of the RAM user. |
|Email|String|alice@example.com|The email address of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|LastLoginDate|String|2020-10-12T09:12:00Z|The last time when the RAM user logged on to the console. |
|MobilePhone|String|86-1868888\*\*\*\*|The mobile phone number of the RAM user.

 **Note:** This parameter applies only to the China site \(aliyun.com\). |
|UpdateDate|String|2020-10-13T09:19:49Z|The time when the information of the RAM user was updated. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListUsers
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListUsersResponse>
	  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
	  <Users>
		    <User>
			      <UpdateDate>2020-10-13T09:19:49Z</UpdateDate>
			      <Email>alice@example.com</Email>
			      <UserId>20732900249392****</UserId>
			      <Comments>This is a cloud computing engineer. </Comments>
			      <DisplayName>test</DisplayName>
			      <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
			      <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
			      <CreateDate>2020-10-12T09:12:00Z</CreateDate>
			      <MobilePhone>86-1868888****</MobilePhone>
		    </User>
	  </Users>
</ListUsersResponse>
```

`JSON` format

```
{
    "RequestId" : "4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
    "IsTruncated": true,
    "Marker": "EXAMPLE",
    "Users" :{  
        "User": [
            {
                "UpdateDate": "2020-10-13T09:19:49Z",
                "Email": "alice@example.com",
                "UserId": "20732900249392****",
                "Comments": "This is a cloud computing engineer.",
                "DisplayName": "test",
                "LastLoginDate": "2020-10-12T09:12:00Z",
                "UserPrincipalName": "test@example.onaliyun.com",
                "CreateDate": "2020-10-12T09:12:00Z",
                "MobilePhone": "86-1868888****"
            }
        ]
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

