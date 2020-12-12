# UpdateGroup

调用UpdateGroup修改指定用户组的信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=UpdateGroup&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateGroup|要执行的操作。取值：UpdateGroup。 |
|GroupName|String|是|Dev-Team|用户组名称。 |
|NewGroupName|String|否|Test-Team|新的用户组名称。

 最大长度64个字符，可包含英文字母、数字、英文句点（.）、下划线（\_）和短划线（-）。 |
|NewDisplayName|String|否|Test-Team|新的用户组显示名称。

 最大长度24个字符。 |
|NewComments|String|否|测试团队|新的备注。

 最大长度128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Group|Struct| |用户组信息。 |
|Comments|String|测试团队|备注。 |
|CreateDate|String|2020-10-19T16:15:17Z|创建时间。 |
|DisplayName|String|Test-Team|用户组显示名称。 |
|GroupId|String|740317625433843\*\*\*\*|用户组ID。 |
|GroupName|String|Test-Team|用户组名称。 |
|UpdateDate|String|2020-10-20T03:44:27Z|更新时间。 |
|RequestId|String|CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=UpdateGroup
&GroupName=Dev-Team
&NewGroupName=Test-Team
&NewDisplayName=Test-Team
&Newcomments=测试团队
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateGroupResponse>
	  <Group>
		    <GroupName>Test-Team</GroupName>
		    <UpdateDate>2020-10-20T03:44:27Z</UpdateDate>
		    <Comments>测试团队</Comments>
            <GroupId>740317625433843****</GroupId>
		    <DisplayName>Test-Team</DisplayName>
		    <CreateDate>2020-10-19T16:15:17Z</CreateDate>
	  </Group>
	  <RequestId>CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287</RequestId>
</UpdateGroupResponse>
```

`JSON` 格式

```
{
  "Group": {
    "GroupName": "Test-Team",
    "UpdateDate": "2020-10-20T03:44:27Z",
    "Comments": "测试团队",
    "GroupId": "740317625433843****",
    "DisplayName": "Test-Team",
    "CreateDate": "2020-10-19T16:15:17Z"
  },
  "RequestId": "CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

