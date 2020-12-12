# CreateAccessKey

调用CreateAccessKey创建阿里云账号（主账号）或RAM用户的访问密钥。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateAccessKey&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAccessKey|要执行的操作。取值：CreateAccessKey。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|RAM用户的登录名称。

 如果为空，默认为当前用户创建访问密钥。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessKey|Struct| |访问密钥。 |
|AccessKeyId|String|LTAI4G3HaMmeHpay2gcq\*\*\*\*|访问密钥ID。 |
|AccessKeySecret|String|Y3MSLE6OgizS4qrz5LVFDoyZEL\*\*\*\*|访问密钥。 |
|CreateDate|String|2020-10-15T08:08:54Z|访问密钥的创建时间。 |
|Status|String|Active|访问密钥的状态。取值：

 -   Active：已激活。
-   Inactive：已禁用。 |
|RequestId|String|19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateAccessKey
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateAccessKeyResponse>
	  <RequestId>19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB</RequestId>
	  <AccessKey>
		    <Status>Active</Status>
		    <AccessKeyId>LTAI4G3HaMmeHpay2gcq****</AccessKeyId>
		    <AccessKeySecret>Y3MSLE6OgizS4qrz5LVFDoyZEL****</AccessKeySecret>
		    <CreateDate>2020-10-15T08:08:54Z</CreateDate>
	  </AccessKey>
</CreateAccessKeyResponse>
```

`JSON` 格式

```
{
  "RequestId": "19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB",
  "AccessKey": {
    "Status": "Active",
    "AccessKeyId": "LTAI4G3HaMmeHpay2gcq****",
    "AccessKeySecret": "Y3MSLE6OgizS4qrz5LVFDoyZEL****",
    "CreateDate": "2020-10-15T08:08:54Z"
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

