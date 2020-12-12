# ListGroupsForUser

调用ListGroupsForUser查询指定RAM用户加入的用户组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListGroupsForUser&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListGroupsForUser|要执行的操作。取值：ListGroupsForUser。 |
|UserPrincipalName|String|是|test@example.onaliyun.com|RAM用户的登录名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Groups|Array of Group| |用户组信息。 |
|Group| | | |
|Comments|String|测试团队|备注。 |
|DisplayName|String|Test-Team|用户组显示名称。 |
|GroupId|String|740317625433843\*\*\*\*|用户组ID。 |
|GroupName|String|Test-Team|用户组名称。 |
|JoinDate|String|2020-10-20T06:57:00Z|RAM用户加入时间。 |
|RequestId|String|7158A935-FB5E-49A7-8E52-FDA5B2B67247|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListGroupsForUser
&UserPrincipalName=test@example.onaliyun.com
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListGroupsForUserResponse>
	  <RequestId>7158A935-FB5E-49A7-8E52-FDA5B2B67247</RequestId>
	  <Groups>
		    <Group>
			      <GroupName>Test-Team</GroupName>
			      <Comments>测试团队</Comments>
                  <GroupId>740317625433843****</GroupId>
			      <DisplayName>Test-Team</DisplayName>
			      <JoinDate>2020-10-20T06:57:00Z</JoinDate>
		    </Group>
	  </Groups>
</ListGroupsForUserResponse>
```

`JSON` 格式

```
{
  "RequestId": "7158A935-FB5E-49A7-8E52-FDA5B2B67247",
  "Groups": {
    "Group": [
      {
        "GroupName": "Test-Team",
        "Comments": "测试团队",
        "GroupId": "740317625433843****",
        "DisplayName": "Test-Team",
        "JoinDate": "2020-10-20T06:57:00Z"
      }
    ]
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

