# ListUsersForGroup

Queries RAM users in a RAM user group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListUsersForGroup&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListUsersForGroup|The operation that you want to perform. Set the value to ListUsersForGroup. |
|GroupName|String|Yes|Test-Team|The name of the RAM user group. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|100|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be `true`.

Valid values: 1 to 100. Default value: 100. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

-   true
-   false |
|Marker|String|EXAMPLE|The `marker`. This parameter is returned only if the value of `IsTruncated` is `true`. If the parameter is returned, you can call this operation again and set this parameter to obtain the truncated part. |
|RequestId|String|789FF581-B3C8-43A8-9115-54304B46D05C|The ID of the request. |
|Users|Array of User| |The information of RAM users. |
|User| | | |
|DisplayName|String|test|The display name of the RAM user. |
|JoinDate|String|2020-10-20T06:57:00Z|The time when the RAM user was added. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListUsersForGroup
&GroupName=Test-Team
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListUsersForGroupResponse>
      <RequestId>789FF581-B3C8-43A8-9115-54304B46D05C</RequestId>
      <IsTruncated>true</IsTruncated>
      <Marker>EXAMPLE</Marker>
      <Users>
            <User>
                  <UserId>20732900249392****</UserId>
                  <DisplayName>test</DisplayName>
                  <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
                  <JoinDate>2020-10-20T06:57:00Z</JoinDate>
            </User>
            <User>
                  <UserId>21096280076542****</UserId>
                  <DisplayName>alice</DisplayName>
                  <UserPrincipalName>alice@example.onaliyun.com</UserPrincipalName>
                  <JoinDate>2020-10-20T07:12:42Z</JoinDate>
            </User>
      </Users>
</ListUsersForGroupResponse>
```

`JSON` format

```
{
  "RequestId": "789FF581-B3C8-43A8-9115-54304B46D05C",
  "IsTruncated": true,
  "Marker": "EXAMPLE",
  "Users": {
    "User": [
      {
        "UserId": "20732900249392****",
        "DisplayName": "test",
        "UserPrincipalName": "test@example.onaliyun.com",
        "JoinDate": "2020-10-20T06:57:00Z"
      },
      {
        "UserId": "21096280076542****",
        "DisplayName": "alice",
        "UserPrincipalName": "alice@example.onaliyun.com",
        "JoinDate": "2020-10-20T07:12:42Z"
      }
    ]
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

