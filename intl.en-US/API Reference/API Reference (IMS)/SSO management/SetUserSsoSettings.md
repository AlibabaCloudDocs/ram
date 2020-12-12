# SetUserSsoSettings

Configures information about identity providers \(IdPs\) for user-based single sign-on \(SSO\).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=SetUserSsoSettings&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetUserSsoSettings|The operation that you want to perform. Set the value to SetUserSsoSettings. |
|MetadataDocument|String|No|PD94bWwgdmVy\*\*\*\*|The metadata file, which is Base64-encoded.

 The file is provided by an IdP that supports SAML 2.0. |
|SsoEnabled|Boolean|No|true|Specifies whether to enable SSO for the RAM user. Default value: false. Valid values:

 -   true
-   false |
|AuxiliaryDomain|String|No|example.com|The auxiliary domain name. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|87F2E3F6-28A0-43F3-A77F-F7760E62F61E|The ID of the request. |
|UserSsoSettings|Struct| |The configurations of user-based SSO. |
|AuxiliaryDomain|String|example.com|The auxiliary domain name. |
|MetadataDocument|String|PD94bWwgdmVy\*\*\*\*|The metadata file, which is Base64-encoded. |
|SsoEnabled|Boolean|true|Indicates whether user-based SSO is enabled. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=SetUserSsoSettings
&MetadataDocument=PD94bWwgdmVy****
&SsoEnabled=true
&AuxiliaryDomain=example.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetUserSsoSettingsResponse>
	  <UserSsoSettings>
		    <MetadataDocument>PD94bWwgdmVy****</MetadataDocument>
		    <SsoEnabled>true</SsoEnabled>
		    <AuxiliaryDomain>example.com</AuxiliaryDomain>
	  </UserSsoSettings>
	  <RequestId>87F2E3F6-28A0-43F3-A77F-F7760E62F61E</RequestId>
</SetUserSsoSettingsResponse>
```

`JSON` format

```
{
  "UserSsoSettings": {
    "MetadataDocument": "PD94bWwgdmVy****",
    "SsoEnabled": true,
    "AuxiliaryDomain": "example.com"
  },
  "RequestId": "87F2E3F6-28A0-43F3-A77F-F7760E62F61E"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

