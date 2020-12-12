# GetAccessKeyLastUsed

Queries the time when an AccessKey pair is used for the last time.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetAccessKeyLastUsed&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetAccessKeyLastUsed|The operation that you want to perform. Set the value to GetAccessKeyLastUsed. |
|UserAccessKeyId|String|Yes|LTAI4GFTgcR8m8cZQDTH\*\*\*\*|The ID of the AccessKey pair that you want to query. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 If this parameter is empty, the AccessKey pair of the current user is queried. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AccessKeyLastUsed|Struct| |The details of the time when the AccessKey pair was used for the last time. |
|LastUsedDate|String|2020-10-16T01:37:37Z|The time when the AccessKey pair was used for the last time. |
|RequestId|String|B29C79F6-354B-4297-A994-1338CC22A2EC|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetAccessKeyLastUsed
&UserAccessKeyId=LTAI4GFTgcR8m8cZQDTH****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetAccessKeyLastUsedResponse>
	  <AccessKeyLastUsed>
		    <LastUsedDate>2020-10-16T01:37:37Z</LastUsedDate>
	  </AccessKeyLastUsed>
	  <RequestId>B29C79F6-354B-4297-A994-1338CC22A2EC</RequestId>
</GetAccessKeyLastUsedResponse>
```

`JSON` format

```
{
  "AccessKeyLastUsed": {
    "LastUsedDate": "2020-10-16T01:37:37Z"
  },
  "RequestId": "B29C79F6-354B-4297-A994-1338CC22A2EC"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

