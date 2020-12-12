# DeleteUser

Deletes a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=DeleteUser&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteUser|The operation that you want to perform. Set the value to DeleteUser. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 **Note:** You must specify only one of the following parameters: `UserPrincipalName` and `UserId`. |
|UserId|String|No|20732900249392\*\*\*\*|The ID of the RAM user.

 **Note:** You must specify only one of the following parameters: `UserPrincipalName` and `UserId`. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=DeleteUser
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteUserResponse>
      <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</DeleteUserResponse>
```

`JSON` format

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

