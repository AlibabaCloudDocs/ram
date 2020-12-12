# SetUserSsoSettings

调用SetUserSsoSettings设置用户SSO身份提供商信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=SetUserSsoSettings&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetUserSsoSettings|要执行的操作。取值：SetUserSsoSettings。 |
|MetadataDocument|String|否|PD94bWwgdmVy\*\*\*\*|元数据文档。经过Base64编码。

 由支持SAML2.0协议的身份提供商提供。 |
|SsoEnabled|Boolean|否|true|是否开启RAM用户的SSO功能。取值：

 -   true：开启。
-   false（默认值）：关闭。 |
|AuxiliaryDomain|String|否|example.com|辅助域名。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|87F2E3F6-28A0-43F3-A77F-F7760E62F61E|请求ID。 |
|UserSsoSettings|Struct| |用户SSO配置信息。 |
|AuxiliaryDomain|String|example.com|辅助域名。 |
|MetadataDocument|String|PD94bWwgdmVy\*\*\*\*|元数据文档。经过Base64编码。 |
|SsoEnabled|Boolean|true|是否开启用户SSO。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=SetUserSsoSettings
&MetadataDocument=PD94bWwgdmVy****
&SsoEnabled=true
&AuxiliaryDomain=example.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

