# CreateGroup

调用CreateGroup创建用户组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateGroup&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateGroup|要执行的操作。取值：CreateGroup。 |
|GroupName|String|是|Dev-Team|用户组名称。该参数必须指定。

 最大长度64个字符，可包含英文字母、数字、英文句点（.）、下划线（\_）和短划线（-）。 |
|DisplayName|String|否|Dev-Team|用户组显示名称。

 最大长度24个字符。 |
|Comments|String|否|开发团队|备注。

 最大长度128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Group|Struct| |用户组信息。 |
|Comments|String|开发团队|备注。 |
|CreateDate|String|2020-10-19T16:15:17Z|创建时间。 |
|DisplayName|String|Dev-Team|用户组显示名称。 |
|GroupId|String|740317625433843\*\*\*\*|用户组ID。 |
|GroupName|String|Dev-Team|用户组名称。 |
|UpdateDate|String|2020-10-19T16:15:17Z|更新时间。 |
|RequestId|String|3C38192B-7BF8-45DA-8F0A-E670EA51426C|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateGroup
&GroupName=Dev-Team
&DisplayName=Dev-Team
&Comments=开发团队
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateGroupResponse>
	  <Group>
		    <GroupName>Dev-Team</GroupName>
		    <UpdateDate>2020-10-19T16:15:17Z</UpdateDate>
            <GroupId>740317625433843****</GroupId>
		    <Comments>开发团队</Comments>
		    <DisplayName>Dev-Team</DisplayName>
		    <CreateDate>2020-10-19T16:15:17Z</CreateDate>
	  </Group>
	  <RequestId>3C38192B-7BF8-45DA-8F0A-E670EA51426C</RequestId>
</CreateGroupResponse>
```

`JSON` 格式

```
{
  "Group": {
    "GroupName": "Dev-Team",
    "UpdateDate": "2020-10-19T16:15:17Z",
    "GroupId": "740317625433843****",
    "Comments": "开发团队",
    "DisplayName": "Dev-Team",
    "CreateDate": "2020-10-19T16:15:17Z"
  },
  "RequestId": "3C38192B-7BF8-45DA-8F0A-E670EA51426C"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

