# GetDefaultDomain

Queries the default domain name.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetDefaultDomain&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetDefaultDomain|The operation that you want to perform. Set the value to GetDefaultDomain. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DefaultDomainName|String|examplecompany.onaliyun.com|The default domain name. |
|RequestId|String|66815255-7CCE-4759-AC37-9755794C3626|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetDefaultDomain
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetDefaultDomainResponse>
        <DefaultDomainName>examplecompany.onaliyun.com</DefaultDomainName>
        <RequestId>66815255-7CCE-4759-AC37-9755794C3626</RequestId>
</GetDefaultDomainResponse>
```

`JSON` format

```
{
  "DefaultDomainName": "examplecompany.onaliyun.com",
  "RequestId": "66815255-7CCE-4759-AC37-9755794C3626"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

