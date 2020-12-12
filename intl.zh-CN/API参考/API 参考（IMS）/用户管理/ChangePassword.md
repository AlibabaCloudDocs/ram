# ChangePassword

RAM用户调用ChangePassword修改自己的控制台登录密码。

**说明：** 该API仅限RAM用户调用。调用前，请确保已将[SetSecurityPreference](~~43765~~)中的`AllowUserToChangePassword`设置为`True`，即允许RAM用户自主管理密码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ChangePassword&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ChangePassword|要执行的操作。取值：ChangePassword。 |
|OldPassword|String|是|mypassword|RAM用户的控制台登录旧密码。 |
|NewPassword|String|是|newpassword|RAM用户的控制台登录新密码。

 密码必须符合密码强度要求。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ChangePassword
&OldPassword=mypassword
&NewPassword=newpassword
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ChangePasswordResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ChangePasswordResponse>
```

`JSON` 格式

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

