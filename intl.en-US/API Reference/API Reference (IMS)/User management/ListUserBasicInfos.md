# ListUserBasicInfos

Queries the basic information of all RAM users.

You can call the following API operations to query the information of all RAM users:

-   ListUsers: queries the details of all RAM users.
-   ListUserBasicInfos: queries the basic information of all RAM users. The basic information includes only the logon names \(`UserPrincipalName`\), display names \(`DisplayName`\), and user IDs \(`UserId`\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListUserBasicInfos&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListUserBasicInfos|The operation that you want to perform. Set the value to ListUserBasicInfos. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|100|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be `true`.

Valid values: 1 to 10. Default value: 100. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

-   true
-   false |
|Marker|String|EXAMPLE|The `marker`. This parameter is returned only if the value of `IsTruncated` is `true`. If the parameter is returned, you can call this operation again and set this parameter to obtain the truncated part. |
|RequestId|String|EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F|The ID of the request. |
|UserBasicInfos|Array of UserBasicInfo| |The basic information of all RAM users. |
|UserBasicInfo| | | |
|DisplayName|String|test|The display name of the RAM user. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@example.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListUserBasicInfos
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListUserBasicInfosResponse>
      <RequestId>EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F</RequestId>
      <IsTruncated>true</IsTruncated>
      <UserBasicInfos>
            <UserBasicInfo>
                  <UserId>20732900249392****</UserId>
                  <DisplayName>test</DisplayName>
                  <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
            </UserBasicInfo>
      </UserBasicInfos>
      <Marker>EXAMPLE</Marker>
</ListUserBasicInfosResponse>
```

`JSON` format

```
{
  "RequestId": "EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F",
  "IsTruncated": true,
  "UserBasicInfos": {
    "UserBasicInfo": [
      {
        "UserId": "20732900249392****",
        "DisplayName": "test",
        "UserPrincipalName": "test@example.onaliyun.com"
      }
    ]
  },
  "Marker": "EXAMPLE"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

