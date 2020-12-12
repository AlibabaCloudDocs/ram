# ListSAMLProviders

调用ListSAMLProviders查询角色SSO身份提供商列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListSAMLProviders&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListSAMLProviders|要执行的操作。取值：ListSAMLProviders。 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。 |
|MaxItems|Integer|否|100|返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1~100。默认值：100。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。取值：

 -   true
-   false |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此参数，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容 。 |
|RequestId|String|2D8B70D3-E194-41C9-93C5-F6A10D716D24|请求ID。 |
|SAMLProviders|Array of SAMLProvider| |身份提供商信息。 |
|SAMLProvider| | | |
|Arn|String|acs:ram::177242285274\*\*\*\*:saml-provider/test-provider|身份提供商的ARN。 |
|CreateDate|String|2020-10-22T06:26:15Z|创建时间。 |
|Description|String|This is a provider.|备注。 |
|SAMLProviderName|String|test-provider|身份提供商名称。 |
|UpdateDate|String|2020-10-22T06:26:15Z|更新时间。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListSAMLProviders
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListSAMLProvidersResponse>
	  <RequestId>2D8B70D3-E194-41C9-93C5-F6A10D716D24</RequestId>
	  <SAMLProviders>
		    <SAMLProvider>
			      <UpdateDate>2020-10-22T06:26:15Z</UpdateDate>
			      <SAMLProviderName>test-provider</SAMLProviderName>
			      <Description>This is a provider.</Description>
			      <Arn>acs:ram::177242285274****:saml-provider/test-provider</Arn>
			      <CreateDate>2020-10-22T06:26:15Z</CreateDate>
		    </SAMLProvider>
	  </SAMLProviders>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
</ListSAMLProvidersResponse>
```

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

