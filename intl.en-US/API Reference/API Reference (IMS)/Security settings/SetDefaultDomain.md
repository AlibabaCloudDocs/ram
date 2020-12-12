# SetDefaultDomain

Configures the default domain name.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=SetDefaultDomain&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetDefaultDomain|The operation that you want to perform. Set the value to SetDefaultDomain. |
|DefaultDomainName|String|Yes|examplecompany.onaliyun.com|The default domain name.

 The name is in the format of `<AccountAlias>.onaliyun.com`. `<AccountAlias>` indicates the account alias. By default, the value of AccountAlias is the ID of the Alibaba Cloud account. The default domain name must end with `.onaliyun.com`.

 The default domain name can contain up to 64 characters in length. The name can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\).

 **Note:** The default domain name cannot start or end with a hyphen \(-\) and cannot have two consecutive hyphens \(-\). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|DefaultDomainName|String|examplecompany.onaliyun.com|The default domain name. |
|RequestId|String|66815255-7CCE-4759-AC37-9755794C3626|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=SetDefaultDomain
&DefaultDomainName=examplecompany.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetDefaultDomainResponse>
	  <DefaultDomainName>examplecompany.onaliyun.com</DefaultDomainName>
	  <RequestId>66815255-7CCE-4759-AC37-9755794C3626</RequestId>
</SetDefaultDomainResponse>
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

