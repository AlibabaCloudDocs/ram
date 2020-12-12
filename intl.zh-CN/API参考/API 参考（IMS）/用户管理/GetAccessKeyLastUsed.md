# GetAccessKeyLastUsed

调用GetAccessKeyLastUsed查询指定访问密钥的最后使用时间。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetAccessKeyLastUsed&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAccessKeyLastUsed|要执行的操作。取值：GetAccessKeyLastUsed。 |
|UserAccessKeyId|String|是|LTAI4GFTgcR8m8cZQDTH\*\*\*\*|需要查询的访问密钥ID。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|RAM用户的登录名称。

 如果为空，默认查询当前用户的访问密钥。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessKeyLastUsed|Struct| |访问密钥的最后使用信息。 |
|LastUsedDate|String|2020-10-16T01:37:37Z|最后使用时间。 |
|RequestId|String|B29C79F6-354B-4297-A994-1338CC22A2EC|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetAccessKeyLastUsed
&UserAccessKeyId=LTAI4GFTgcR8m8cZQDTH****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetAccessKeyLastUsedResponse>
	  <AccessKeyLastUsed>
		    <LastUsedDate>2020-10-16T01:37:37Z</LastUsedDate>
	  </AccessKeyLastUsed>
	  <RequestId>B29C79F6-354B-4297-A994-1338CC22A2EC</RequestId>
</GetAccessKeyLastUsedResponse>
```

`JSON` 格式

```
{
  "AccessKeyLastUsed": {
    "LastUsedDate": "2020-10-16T01:37:37Z"
  },
  "RequestId": "B29C79F6-354B-4297-A994-1338CC22A2EC"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

