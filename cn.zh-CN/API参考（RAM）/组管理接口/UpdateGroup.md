# UpdateGroup

调用UpdateGroup接口修改用户组信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateGroup&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateGroup|要执行的操作。取值：UpdateGroup。 |
|GroupName|String|是|Dev-Team|用户组名称。 |
|NewGroupName|String|否|NewDev-Team|新的用户组名称。

 长度为1~64个字符，可包含英文字母、数字、英文句点（.）、下划线（\_）和短划线（-）。 |
|NewComments|String|否|开发团队|新的备注信息。

 长度为1~128个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Group|Struct| |用户组信息。 |
|Comments|String|开发团队|备注信息。 |
|CreateDate|String|2015-01-23T12:33:18Z|创建时间。 |
|GroupId|String|g-FpMEHiMysofp\*\*\*\*|用户组ID。 |
|GroupName|String|NewDev-Team|用户组名称。 |
|UpdateDate|String|2015-01-23T12:33:18Z|更新时间。 |
|RequestId|String|EC6647CC-0A36-EC7A-BA72-CC81BF3DE182|请求ID。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=UpdateGroup
&GroupName=Dev-Team
&NewGroupName=NewDev-Team
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateGroupResponse>
	  <RequestId>EC6647CC-0A36-EC7A-BA72-CC81BF3DE182</RequestId>
	  <Group>
		    <GroupName>NewDev-Team</GroupName>
		    <Comments>开发团队</Comments>
		    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
		    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
            <GroupId>g-FpMEHiMysofp****</GroupId>
	  </Group>
</UpdateGroupResponse>
```

`JSON` 格式

```
{
    "RequestId": "EC6647CC-0A36-EC7A-BA72-CC81BF3DE182",
    "Group": {
        "GroupName": "NewDev-Team",
        "Comments": "开发团队",
        "CreateDate" : "2015-01-23T12:33:18Z",
        "UpdateDate" : "2015-01-23T12:33:18Z",
        "GroupId": "g-FpMEHiMysofp****"
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

