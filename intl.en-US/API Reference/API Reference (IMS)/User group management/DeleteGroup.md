# DeleteGroup

Deletes a RAM user group.

Before you delete a RAM user group, make sure that no policies are attached to the group and no RAM users are included in the group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=DeleteGroup&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteGroup|The operation that you want to perform. Set the value to DeleteGroup. |
|GroupName|String|Yes|Dev-Team|The name of the RAM user group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=DeleteGroup
&GroupName=Dev-Team
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteGroupResponse>
        <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</DeleteGroupResponse>
```

`JSON` format

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

