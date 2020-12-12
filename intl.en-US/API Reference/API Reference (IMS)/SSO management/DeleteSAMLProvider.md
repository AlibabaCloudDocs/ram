# DeleteSAMLProvider

Deletes an identity provider \(IdP\) for role-based SSO.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=DeleteSAMLProvider&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteSAMLProvider|The operation that you want to perform. Set the value to DeleteSAMLProvider. |
|SAMLProviderName|String|Yes|test-provider|The name of the IdP that you want to delete. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|85836703-8D4F-485F-9726-4D1C730F957E|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=DeleteSAMLProvider
&SAMLProviderName=test-provider
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteSAMLProviderResponse>
          <RequestId>85836703-8D4F-485F-9726-4D1C730F957E</RequestId>
</DeleteSAMLProviderResponse>
```

`JSON` format

```
{
  "RequestId": "85836703-8D4F-485F-9726-4D1C730F957E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

