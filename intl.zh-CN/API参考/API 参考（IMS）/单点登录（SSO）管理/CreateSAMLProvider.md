# CreateSAMLProvider

调用CreateSAMLProvider创建角色SSO身份提供商。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateSAMLProvider&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSAMLProvider|要执行的操作。取值：CreateSAMLProvider。 |
|EncodedSAMLMetadataDocument|String|是|PD94bWwgdmVy\*\*\*\*|元数据文档。经过Base64编码。

 由支持SAML2.0协议的身份提供商提供。 |
|SAMLProviderName|String|是|test-provider|身份提供商名称。

 最大长度128个字符，允许英文字母、数字、特殊字符`.-_`，不能以特殊字符`.-_`开头或结尾。 |
|Description|String|否|This is a provider.|备注。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|请求ID。|请求ID。 |
|SAMLProvider|Struct| |身份提供商信息。 |
|Arn|String|acs:ram::177242285274\*\*\*\*:saml-provider/test-provider|身份提供商的ARN。 |
|CreateDate|String|2020-10-22T02:37:05Z|创建时间。 |
|Description|String|This is a provider.|备注。 |
|SAMLProviderName|String|test-provider|身份提供商名称。 |
|UpdateDate|String|2020-10-22T02:51:20Z|更新时间。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateSAMLProvider
EncodedSAMLMetadataDocument=PD94bWwgdmVy****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateSAMLProviderResponse>
        <RequestId>E5EDDFD2-3654-4F9F-9780-4AE7D81823EF</RequestId>
        <SAMLProvider>
                <UpdateDate>2020-10-22T02:51:20Z</UpdateDate>
                <SAMLProviderName>test-provider</SAMLProviderName>
                <Description>This is a provider.</Description>
                <Arn>acs:ram::177242285274****:saml-provider/test-provider</Arn>
                <CreateDate>2020-10-22T02:37:05Z</CreateDate>
        </SAMLProvider>
</CreateSAMLProviderResponse>
```

`JSON` 格式

```
{
  "RequestId": "E5EDDFD2-3654-4F9F-9780-4AE7D81823EF",
  "SAMLProvider": {
    "UpdateDate": "2020-10-22T02:51:20Z",
    "SAMLProviderName": "test-provider",
    "Description": "This is a provider.",
    "Arn": "acs:ram::177242285274****:saml-provider/test-provider",
    "CreateDate": "2020-10-22T02:37:05Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

