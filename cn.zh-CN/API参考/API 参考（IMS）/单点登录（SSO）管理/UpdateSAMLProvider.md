# UpdateSAMLProvider

调用UpdateSAMLProvider修改指定的角色SSO身份提供商信息。

本文将提供一个示例，为`test-provider`身份提供商修改备注信息为`This is a new provider.`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=UpdateSAMLProvider&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateSAMLProvider|要执行的操作。取值：**UpdateSAMLProvider**。 |
|SAMLProviderName|String|是|test-provider|需要修改的身份提供商名称。 |
|NewDescription|String|否|This is a new provider.|新的备注。

 **说明：** `NewDescription`与`NewEncodedSAMLMetadataDocument`参数必须至少填写一个。 |
|NewEncodedSAMLMetadataDocument|String|否|PD94bWwgdmVy\*\*\*\*|新的元数据文档。

 **说明：** `NewDescription`与`NewEncodedSAMLMetadataDocument`参数必须至少填写一个。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E5EDDFD2-3654-4F9F-9780-4AE7D81823EF|请求ID。 |
|SAMLProvider|Object| |身份提供商信息。 |
|UpdateDate|String|2020-10-22T02:51:20Z|身份提供商的修改时间（UTC时间）。 |
|Description|String|This is a new provider.|备注。 |
|SAMLProviderName|String|test-provider|身份提供商名称。 |
|CreateDate|String|2020-10-22T02:37:05Z|身份提供商的创建时间（UTC时间）。 |
|Arn|String|acs:ram::177242285274\*\*\*\*:saml-provider/test-provider|身份提供商ARN。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=UpdateSAMLProvider
&SAMLProviderName=test-provider
&NewDescription=This is a new provider.
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<UpdateSAMLProviderResponse>
        <RequestId>E5EDDFD2-3654-4F9F-9780-4AE7D81823EF</RequestId>
        <SAMLProvider>
                <UpdateDate>2020-10-22T02:51:20Z</UpdateDate>
                <SAMLProviderName>test-provider</SAMLProviderName>
                <Description>This is a new provider.</Description>
                <Arn>acs:ram::177242285274****:saml-provider/test-provider</Arn>
                <CreateDate>2020-10-22T02:37:05Z</CreateDate>
        </SAMLProvider>
</UpdateSAMLProviderResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "E5EDDFD2-3654-4F9F-9780-4AE7D81823EF",
  "SAMLProvider" : {
    "UpdateDate" : "2020-10-22T02:51:20Z",
    "SAMLProviderName" : "test-provider",
    "Description" : "This is a new provider.",
    "Arn" : "acs:ram::177242285274****:saml-provider/test-provider",
    "CreateDate" : "2020-10-22T02:37:05Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

