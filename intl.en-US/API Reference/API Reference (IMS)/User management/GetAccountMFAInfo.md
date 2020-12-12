# GetAccountMFAInfo

Queries a multi-factor authentication \(MFA\) device of an Alibaba Cloud account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetAccountMFAInfo&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetAccountMFAInfo|The operation that you want to perform. Set the value to GetAccountMFAInfo. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsMFAEnable|Boolean|false|Indicates whether MFA is enabled. Valid values:

 -   true
-   false |
|RequestId|String|4BE83135-0B08-467C-B3A2-27B312FD0F57|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetAccountMFAInfo
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetAccountMFAInfoResponse>
	  <RequestId>4BE83135-0B08-467C-B3A2-27B312FD0F57</RequestId>
	  <IsMFAEnable>false</IsMFAEnable>
</GetAccountMFAInfoResponse>
```

`JSON` format

```
{
  "RequestId": "4BE83135-0B08-467C-B3A2-27B312FD0F57",
  "IsMFAEnable": false
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

