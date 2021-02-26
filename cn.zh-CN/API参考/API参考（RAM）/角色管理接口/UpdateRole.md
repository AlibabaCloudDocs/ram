# UpdateRole

调用UpdateRole接口更新RAM角色信息。

本文将提供一个示例，更新RAM角色`ECSAdmin`的描述信息为`ECS管理员`。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ram&api=UpdateRole&type=RPC&version=2015-05-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateRole|要执行的操作。取值：UpdateRole。 |
|RoleName|String|是|ECSAdmin|RAM角色名称。

 长度为1~64个字符，可包含英文字母、数字、半角句号（.）和短划线（-）。 |
|NewAssumeRolePolicyDocument|String|否|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::12345678901234\*\*\*\*:root" \} \} \], "Version": "1" \}|RAM角色的信任策略。 |
|NewMaxSessionDuration|Long|否|3600|RAM角色最大会话时间。

 取值范围：3600秒~43200秒。默认值：3600秒。

 取值为空时将采用默认值。 |
|NewDescription|String|否|ECS管理角色|RAM角色描述。

 长度为1~1024个字符。 |

关于公共请求参数的详情，请参见[公共参数](~~28676~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |
|Role|Struct| |RAM角色信息。 |
|Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|RAM角色的资源描述符。 |
|AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|RAM角色的信任策略。 |
|CreateDate|String|2015-01-23T12:33:18Z|RAM角色的创建时间。 |
|Description|String|ECS管理角色|RAM角色描述。 |
|MaxSessionDuration|Long|3600|RAM角色最大会话时间。 |
|RoleId|String|901234567890\*\*\*\*|RAM角色ID。 |
|RoleName|String|ECSAdmin|RAM角色名称。 |
|UpdateDate|String|2015-01-23T12:33:18Z|RAM角色的更新时间。 |

## 示例

请求示例

```
https://ram.aliyuncs.com/?Action=UpdateRole
&RoleName=ECSAdmin
&NewDescription=ECS管理角色
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<UpdateRoleResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
	  <Role>
		    <RoleId>901234567890****</RoleId>
		    <RoleName>ECSAdmin</RoleName>
		    <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
		    <Description>ECS管理角色</Description>
		    <MaxSessionDuration>3600</MaxSessionDuration>
		    <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
		    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
		    <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
	  </Role>
</UpdateRoleResponse>
```

`JSON`格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "Role": {
        "RoleId": "901234567890****",
        "RoleName": "ECSAdmin",
        "Arn": "acs:ram::123456789012****:role/ECSAdmin",
        "Description": "ECS管理角色",
        "MaxSessionDuration": 3600,
        "AssumeRolePolicyDocument": "{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
        "CreateDate": "2015-01-23T12:33:18Z",
        "UpdateDate": "2015-01-23T12:33:18Z"
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ram)查看更多错误码。

