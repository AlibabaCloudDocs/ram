# SetDefaultDomain

调用SetDefaultDomain设置默认域名。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=SetDefaultDomain&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetDefaultDomain|要执行的操作。取值：SetDefaultDomain。 |
|DefaultDomainName|String|是|examplecompany.onaliyun.com|默认域名。

 格式：`<AccountAlias>.onaliyun.com`。其中`<AccountAlias>`为账号别名，默认值是阿里云账号ID。默认域名必须以`.onaliyun.com`后缀结尾。

 默认域名（含后缀）最大长度为64个字符。可包含英文字母、数字、英文句点（.）、短划线（-）和下划线（\_）。

 **说明：** 默认域名不能以短划线（-）开头或结尾，且不能有两个连续的短划线（-）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|DefaultDomainName|String|examplecompany.onaliyun.com|默认域名。 |
|RequestId|String|66815255-7CCE-4759-AC37-9755794C3626|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=SetDefaultDomain
&DefaultDomainName=examplecompany.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetDefaultDomainResponse>
	  <DefaultDomainName>examplecompany.onaliyun.com</DefaultDomainName>
	  <RequestId>66815255-7CCE-4759-AC37-9755794C3626</RequestId>
</SetDefaultDomainResponse>
```

`JSON` 格式

```
{
  "DefaultDomainName": "examplecompany.onaliyun.com",
  "RequestId": "66815255-7CCE-4759-AC37-9755794C3626"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

