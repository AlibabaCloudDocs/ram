# GetUserSsoSettings

调用GetUserSsoSettings查询用户SSO身份提供商信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetUserSsoSettings&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetUserSsoSettings|要执行的操作。取值：GetUserSsoSettings。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|69FC3E5E-D3D9-434B-90CA-BBA8E0551A47|请求ID。 |
|UserSsoSettings|Struct| |用户SSO配置信息。 |
|AuxiliaryDomain|String|example.com|辅助域名。 |
|MetadataDocument|String|PD94bWwgdmVy\*\*\*\*|元数据文档。经过Base64编码。 |
|SsoEnabled|Boolean|false|是否开启用户SSO。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetUserSsoSettings
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

