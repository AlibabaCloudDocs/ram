# ListUsers

调用ListUsers查询所有RAM用户的详细信息。

您可以通过以下两个API查询所有RAM用户的信息，区别如下：

-   ListUsers：查询RAM用户的详细信息。
-   ListUserBasicInfos：查询RAM用户的基本信息，仅包括RAM用户登录名称`UserPrincipalName`、RAM用户显示名称`DisplayName`和RAM用户ID`UserId`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListUsers&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUsers|要执行的操作。取值：ListUsers。 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。 |
|MaxItems|Integer|否|1000|返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于true。

 取值范围：1~1000。默认值：1000。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。取值：

 -   true
-   false |
|Marker|String|EXAMPLE|此参数在`IsTruncated`为`true`时生效，用于获取截断后的内容。 |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|请求ID。 |
|Users|Array of User| |RAM用户信息。 |
|User| | | |
|Comments|String|This is a cloud computing engineer.|备注。 |
|CreateDate|String|2020-10-12T09:12:00Z|RAM用户的创建时间。 |
|DisplayName|String|test|RAM用户的显示名称。 |
|Email|String|alice@example.com|RAM用户的电子邮箱。

 **说明：** 该参数仅适用于中国站。 |
|LastLoginDate|String|2020-10-12T09:12:00Z|RAM用户最近一次登录控制台的时间。 |
|MobilePhone|String|86-1868888\*\*\*\*|RAM用户的手机号码。

 **说明：** 该参数仅适用于中国站。 |
|UpdateDate|String|2020-10-13T09:19:49Z|RAM用户的更新时间。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListUsers
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListUsersResponse>
	  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
	  <Users>
		    <User>
			      <UpdateDate>2020-10-13T09:19:49Z</UpdateDate>
			      <Email>alice@example.com</Email>
			      <UserId>20732900249392****</UserId>
			      <Comments>This is a cloud computing engineer.</Comments>
			      <DisplayName>test</DisplayName>
			      <LastLoginDate>2020-10-12T09:12:00Z</LastLoginDate>
			      <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
			      <CreateDate>2020-10-12T09:12:00Z</CreateDate>
			      <MobilePhone>86-1868888****</MobilePhone>
		    </User>
	  </Users>
</ListUsersResponse>
```

`JSON` 格式

```
{
    "RequestId" : "4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
    "IsTruncated": true,
    "Marker": "EXAMPLE",
    "Users" :{  
        "User": [
            {
                "UpdateDate": "2020-10-13T09:19:49Z",
                "Email": "alice@example.com",
                "UserId": "20732900249392****",
                "Comments": "This is a cloud computing engineer.",
                "DisplayName": "test",
                "LastLoginDate": "2020-10-12T09:12:00Z",
                "UserPrincipalName": "test@example.onaliyun.com",
                "CreateDate": "2020-10-12T09:12:00Z",
                "MobilePhone": "86-1868888****"
            }
        ]
    }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

