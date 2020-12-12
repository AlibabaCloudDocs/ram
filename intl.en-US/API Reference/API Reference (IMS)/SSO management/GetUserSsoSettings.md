# GetUserSsoSettings

Queries information about identity providers \(IdPs\) for user-based single sign-on \(SSO\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetUserSsoSettings&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetUserSsoSettings|The operation that you want to perform. Set the value to GetUserSsoSettings. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|69FC3E5E-D3D9-434B-90CA-BBA8E0551A47|The ID of the request. |
|UserSsoSettings|Struct| |The configurations of user-based SSO. |
|AuxiliaryDomain|String|example.com|The auxiliary domain name. |
|MetadataDocument|String|PD94bWwgdmVy\*\*\*\*|The metadata file, which is Base64-encoded. |
|SsoEnabled|Boolean|false|Indicates whether user-based SSO is enabled. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetUserSsoSettings
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetUserSsoSettingsResponse>
	  <UserSsoSettings>
		    <MetadataDocument>PD94bWwgdmVy****</MetadataDocument>
		    <SsoEnabled>false</SsoEnabled>
		    <AuxiliaryDomain>example.com</AuxiliaryDomain>
	  </UserSsoSettings>
	  <RequestId>69FC3E5E-D3D9-434B-90CA-BBA8E0551A47</RequestId>
</GetUserSsoSettingsResponse>
```

`JSON` format

```
{
  "UserSsoSettings": {
    "MetadataDocument": "PD94bWwgdmVy****",
    "SsoEnabled": false,
    "AuxiliaryDomain": "example.com"
  },
  "RequestId": "69FC3E5E-D3D9-434B-90CA-BBA8E0551A47"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

