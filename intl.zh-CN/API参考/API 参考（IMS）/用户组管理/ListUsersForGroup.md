# ListUsersForGroup

调用ListUsersForGroup查询指定用户组内的RAM用户列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListUsersForGroup&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUsersForGroup|要执行的操作。取值：ListUsersForGroup。 |
|GroupName|String|是|Test-Team|用户组名称。 |
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
|RequestId|String|789FF581-B3C8-43A8-9115-54304B46D05C|请求ID。 |
|Users|Array of User| |RAM用户信息。 |
|User| | | |
|DisplayName|String|test|RAM用户的显示名称。 |
|JoinDate|String|2020-10-20T06:57:00Z|RAM用户的加入时间。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|test@example.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListUsersForGroup
&GroupName=Test-Team
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListUsersForGroupResponse>
	  <RequestId>789FF581-B3C8-43A8-9115-54304B46D05C</RequestId>
      <IsTruncated>true</IsTruncated>
      <Marker>EXAMPLE</Marker>
	  <Users>
		    <User>
			      <UserId>20732900249392****</UserId>
			      <DisplayName>test</DisplayName>
			      <UserPrincipalName>test@example.onaliyun.com</UserPrincipalName>
			      <JoinDate>2020-10-20T06:57:00Z</JoinDate>
		    </User>
		    <User>
			      <UserId>21096280076542****</UserId>
			      <DisplayName>alice</DisplayName>
			      <UserPrincipalName>alice@example.onaliyun.com</UserPrincipalName>
			      <JoinDate>2020-10-20T07:12:42Z</JoinDate>
		    </User>
	  </Users>
</ListUsersForGroupResponse>
```

`JSON` 格式

```
{
  "RequestId": "789FF581-B3C8-43A8-9115-54304B46D05C",
  "IsTruncated": true,
  "Marker": "EXAMPLE",
  "Users": {
    "User": [
      {
        "UserId": "20732900249392****",
        "DisplayName": "test",
        "UserPrincipalName": "test@example.onaliyun.com",
        "JoinDate": "2020-10-20T06:57:00Z"
      },
      {
        "UserId": "21096280076542****",
        "DisplayName": "alice",
        "UserPrincipalName": "alice@example.onaliyun.com",
        "JoinDate": "2020-10-20T07:12:42Z"
      }
    ]
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

