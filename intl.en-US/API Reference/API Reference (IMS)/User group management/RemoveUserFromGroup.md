# RemoveUserFromGroup

Removes a RAM user from a RAM user group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=RemoveUserFromGroup&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RemoveUserFromGroup|The operation that you want to perform. Set the value to RemoveUserFromGroup. |
|GroupName|String|Yes|Test-Team|The name of the RAM user group. |
|UserPrincipalName|String|Yes|alice@example.onaliyun.com|The logon name of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=RemoveUserFromGroup
&GroupName=Test-Team
&UserPrincipalName=alice@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RemoveUserFromGroupResponse>
          <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</RemoveUserFromGroupResponse>
```

`JSON` format

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

