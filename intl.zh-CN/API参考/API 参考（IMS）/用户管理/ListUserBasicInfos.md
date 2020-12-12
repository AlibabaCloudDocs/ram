# ListUserBasicInfos

调用ListUserBasicInfos查询所有RAM用户的基本信息。

您可以通过以下两个API查询所有RAM用户的信息，区别如下：

-   ListUsers：查询RAM用户的详细信息。
-   ListUserBasicInfos：查询RAM用户的基本信息，仅包括RAM用户登录名称`UserPrincipalName`、RAM用户显示名称`DisplayName`和RAM用户ID`UserId`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListUserBasicInfos&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUserBasicInfos|要执行的操作。取值：ListUserBasicInfos。 |
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
|RequestId|String|EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F|请求ID。 |
|UserBasicInfos|Array of UserBasicInfo| |RAM用户的基本信息。 |
|UserBasicInfo| | | |
|DisplayName|String|test|RAM用户的显示名称。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListUserBasicInfos
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListUserBasicInfosResponse>
	  <RequestId>EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F</RequestId>
	  <IsTruncated>true</IsTruncated>
	  <UserBasicInfos>
		    <UserBasicInfo>
			      <UserId>20732900249392****</UserId>
			      <DisplayName>test</DisplayName>
			      <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
		    </UserBasicInfo>
	  </UserBasicInfos>
	  <Marker>EXAMPLE</Marker>
</ListUserBasicInfosResponse>
```

`JSON` 格式

```
{
  "RequestId": "EF2B25FD-CADE-445B-BE4D-E082E0FF1A0F",
  "IsTruncated": true,
  "UserBasicInfos": {
    "UserBasicInfo": [
      {
        "UserId": "20732900249392****",
        "DisplayName": "test",
        "UserPrincipalName": "test@example.onaliyun.com"
      }
    ]
  },
  "Marker": "EXAMPLE"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

