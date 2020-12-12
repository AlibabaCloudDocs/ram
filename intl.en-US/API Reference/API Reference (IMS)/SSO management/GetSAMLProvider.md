# GetSAMLProvider

Queries identity providers \(IdPs\) for role-based SSO.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetSAMLProvider&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetSAMLProvider|The operation that you want to perform. Set the value to GetSAMLProvider. |
|SAMLProviderName|String|Yes|test-provider|The name of the IdP. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|BAADB995-0C7A-476D-B293-7E94568EEDFB|The ID of the request. |
|SAMLProvider|Struct| |The information of the IdP. |
|Arn|String|acs:ram::177242285274\*\*\*\*:saml-provider/test-provider|The Alibaba Cloud Resource Name \(ARN\) of the IdP. |
|CreateDate|String|2020-10-22T02:37:05Z|The creation time. |
|Description|String|This is a provider.|The description. |
|EncodedSAMLMetadataDocument|String|PD94bWwgdmVy\*\*\*\*|The metadata file, which is Base64 encoded. |
|SAMLProviderName|String|test-provider|The name of the IdP. |
|UpdateDate|String|2020-10-22T02:51:20Z|The update time. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetSAMLProvider
&SAMLProviderName=test-provider
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetSAMLProviderResponse>
	  <RequestId>E5EDDFD2-3654-4F9F-9780-4AE7D81823EF</RequestId>
	  <SAMLProvider>
		    <UpdateDate>2020-10-22T02:51:20Z</UpdateDate>
		    <SAMLProviderName>test-provider</SAMLProviderName>
		    <Description>This is a provider. </Description>
		    <EncodedSAMLMetadataDocument>PD94bWwgdmVy****</EncodedSAMLMetadataDocument>
		    <Arn>acs:ram::177242285274****:saml-provider/test-provider</Arn>
		    <CreateDate>2020-10-22T02:37:05Z</CreateDate>
	  </SAMLProvider>
</GetSAMLProviderResponse>
```

`JSON` format

```
{
  "RequestId": "E5EDDFD2-3654-4F9F-9780-4AE7D81823EF",
  "SAMLProvider": {
    "UpdateDate": "2020-10-22T02:51:20Z",
    "SAMLProviderName": "test-provider",
    "Description": "This is a provider.",
    "EncodedSAMLMetadataDocument": "PD94bWwgdmVy****",
    "Arn": "acs:ram::177242285274****:saml-provider/test-provider",
    "CreateDate": "2020-10-22T02:37:05Z"
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

