# ListAccessKeys

调用ListAccessKeys查询阿里云账号（主账号）或RAM用户的访问密钥列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListAccessKeys&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAccessKeys|要执行的操作。取值：ListAccessKeys。 |
|UserPrincipalName|String|否|test@example.onaliyun.com|RAM用户的登录名称。

 如果为空，默认查询当前用户的所有访问密钥。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessKeys|Array of AccessKey| |访问密钥信息。 |
|AccessKey| | | |
|AccessKeyId|String|0wNEpMMlzy7s\*\*\*\*|访问密钥ID。 |
|CreateDate|String|2020-10-13T12:33:18Z|访问密钥创建时间。 |
|Status|String|Active|访问密钥状态。取值：

 -   Active：已激活。
-   Inactive：已禁用。 |
|UpdateDate|String|2020-10-13T12:33:18Z|访问密钥更新时间。 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListAccessKeys
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListAccessKeysResponse>
	  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
	  <AccessKeys>
		    <AccessKey>
			      <AccessKeyId>0wNEpMMlzy7s****</AccessKeyId>
			      <Status>Active</Status>
			      <CreateDate>2020-10-13T12:33:18Z</CreateDate>
			      <UpdateDate>2020-10-13T12:33:18Z</UpdateDate>
		    </AccessKey>
		    <AccessKey>
			      <AccessKeyId>WnIWUruvfaDT****</AccessKeyId>
			      <Status>Inactive</Status>
			      <CreateDate>2020-10-14T12:33:18Z</CreateDate>
			      <UpdateDate>2020-10-14T21:12:21Z</UpdateDate>
		    </AccessKey>
	  </AccessKeys>
</ListAccessKeysResponse>
```

`JSON` 格式

```
{
  "RequestId" : "4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
  "AccessKeys":{
    "AccessKey":[
      {
        "AccessKeyId": "0wNEpMMlzy7s****",
        "Status": "Active",
        "CreateDate": "2020-10-13T12:33:18Z",
        "UpdateDate": "2020-10-13T12:33:18Z"
      },
      {
        "AccessKeyId": "WnIWUruvfaDT****",
        "Status": "Inactive",
        "CreateDate": "2020-10-14T12:33:18Z",
        "UpdateDate": "2020-10-14T21:12:21Z"
      }
    ]
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

