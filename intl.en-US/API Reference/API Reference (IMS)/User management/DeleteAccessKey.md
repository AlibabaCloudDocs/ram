# DeleteAccessKey

Deletes an AccessKey pair from an Alibaba Cloud account or a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=DeleteAccessKey&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteAccessKey|The operation that you want to perform. Set the value to DeleteAccessKey. |
|UserAccessKeyId|String|Yes|LTAI4GFTgcR8m8cZQDTH\*\*\*\*|The ID of the AccessKey pair that you want to delete. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 If this parameter is empty, the AccessKey pair of the current user is deleted. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=DeleteAccessKey
&UserAccessKeyId=LTAI4GFTgcR8m8cZQDTH****
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteAccessKeyResponse>
          <RequestId>B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC</RequestId>
</DeleteAccessKeyResponse>
```

`JSON` format

```
{
  "RequestId": "B9AF80E4-1565-42D9-9256-0B8B0D9FD3EC"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

