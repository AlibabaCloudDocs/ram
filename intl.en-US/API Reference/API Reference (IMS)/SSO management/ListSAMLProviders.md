# ListSAMLProviders

Queries identity providers \(IdPs\) for role-based SSO.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListSAMLProviders&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListSAMLProviders|The operation that you want to perform. Set the value to ListSAMLProviders. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|100|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be `true`.

Valid values: 1 to 100. Default value: 100. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

-   true
-   false |
|Marker|String|EXAMPLE|The `marker`. This parameter is returned only if the value of `IsTruncated` is `true`. If the parameter is returned, you can call this operation again and set this parameter to obtain the truncated part. |
|RequestId|String|2D8B70D3-E194-41C9-93C5-F6A10D716D24|The ID of the request. |
|SAMLProviders|Array of SAMLProvider| |The information of the IdP. |
|SAMLProvider| | | |
|Arn|String|acs:ram::177242285274\*\*\*\*:saml-provider/test-provider|The Alibaba Cloud Resource Name \(ARN\) of the IdP. |
|CreateDate|String|2020-10-22T06:26:15Z|The creation time. |
|Description|String|This is a provider.|The description. |
|SAMLProviderName|String|test-provider|The name of the IdP. |
|UpdateDate|String|2020-10-22T06:26:15Z|The update time. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListSAMLProviders
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListSAMLProvidersResponse>
      <RequestId>2D8B70D3-E194-41C9-93C5-F6A10D716D24</RequestId>
      <SAMLProviders>
            <SAMLProvider>
                  <UpdateDate>2020-10-22T06:26:15Z</UpdateDate>
                  <SAMLProviderName>test-provider</SAMLProviderName>
                  <Description>This is a provider. </Description>
                  <Arn>acs:ram::177242285274****:saml-provider/test-provider</Arn>
                  <CreateDate>2020-10-22T06:26:15Z</CreateDate>
            </SAMLProvider>
      </SAMLProviders>
      <IsTruncated>true</IsTruncated>
      <Marker>EXAMPLE</Marker>
</ListSAMLProvidersResponse>
```

`JSON` format

```
{
  "RequestId": "2D8B70D3-E194-41C9-93C5-F6A10D716D24",
  "SAMLProviders": {
    "SAMLProvider": [
      {
        "UpdateDate": "2020-10-22T06:26:15Z",
        "SAMLProviderName": "test-provider",
        "Description": "This is a provider.",
        "Arn": "acs:ram::177242285274****:saml-provider/test-provider",
        "CreateDate": "2020-10-22T06:26:15Z"
      }
    ]
  },
  "IsTruncated": true,
  "Marker": "EXAMPLE"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

