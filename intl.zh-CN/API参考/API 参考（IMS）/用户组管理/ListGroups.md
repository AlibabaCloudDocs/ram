# ListGroups

调用ListGroups查询用户组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListGroups&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListGroups|要执行的操作。取值：ListGroups。 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。 |
|MaxItems|Integer|否|100|返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1~100。默认值：100。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Groups|Array of Group| |用户组信息。 |
|Group| | | |
|Comments|String|开发团队|备注。 |
|CreateDate|String|2020-10-19T12:33:18Z|创建时间。 |
|DisplayName|String|Dev-Team|用户组显示名称。 |
|GroupId|String|740317625433843\*\*\*\*|用户组ID。 |
|GroupName|String|dev-team|用户组名称。 |
|UpdateDate|String|2020-10-19T12:33:18Z|更新时间。 |
|IsTruncated|Boolean|true|请求返回结果是否被截断。取值：

 -   true
-   false |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此参数，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容 。 |
|RequestId|String|065527AA-2F2E-AD7C-7484-F2626CFE4934|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListGroups
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListGroupsResponse>
	  <Groups>
		    <Group>
			      <Comments>开发团队</Comments>
			      <CreateDate>2020-10-19T12:33:18Z</CreateDate>
			      <DisplayName>Dev-Team</DisplayName>
			      <GroupName>Dev-Team</GroupName>
                  <GroupId>740317625433843****</GroupId>
			      <UpdateDate>2020-10-19T12:33:18Z</UpdateDate>
		    </Group>
	  </Groups>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
	  <RequestId>065527AA-2F2E-AD7C-7484-F2626CFE4934</RequestId>
</ListGroupsResponse>
```

`JSON` 格式

```
{
  "Groups": {
    "Group": [
      {
        "Comments": "开发团队",
        "CreateDate": "2020-10-19T12:33:18Z",
        "DisplayName": "Dev-Team",
        "GroupName": "Dev-Team",
        "GroupId": "740317625433843****",
        "UpdateDate": "2020-10-19T12:33:18Z"
      }
    ]
  },
  "IsTruncated": true,
  "Marker": "EXAMPLE",
  "RequestId": "065527AA-2F2E-AD7C-7484-F2626CFE4934"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

