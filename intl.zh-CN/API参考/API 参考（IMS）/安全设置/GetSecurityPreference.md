# GetSecurityPreference

调用GetSecurityPreference查询RAM用户的全局安全首选项。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetSecurityPreference&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetSecurityPreference|要执行的操作。取值：GetSecurityPreference。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|30C9068D-FBAA-4998-9986-8A562FED0BC3|请求ID。 |
|SecurityPreference|Struct| |安全首选项信息。 |
|AccessKeyPreference|Struct| |访问密钥首选项。 |
|AllowUserToManageAccessKeys|Boolean|false|是否允许RAM用户自主管理访问密钥。 |
|LoginProfilePreference|Struct| |登录首选项。 |
|AllowUserToChangePassword|Boolean|true|是否允许RAM用户自主管理密码。 |
|EnableSaveMFATicket|Boolean|false|是否允许RAM用户在登录时保存多因素设备认证状态。如果为允许（true），则7天内不用验证MFA。 |
|LoginNetworkMasks|String|10.0.0.0/8|登录掩码。 |
|LoginSessionDuration|Integer|6|RAM用户登录有效期。 |
|MFAPreference|Struct| |多因素认证首选项。 |
|AllowUserToManageMFADevices|Boolean|false|是否允许RAM用户自主管理多因素认证设备。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetSecurityPreference
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetSecurityPreferenceResponse>
	  <SecurityPreference>
		    <LoginProfilePreference>
			      <LoginSessionDuration>6</LoginSessionDuration>
			      <LoginNetworkMasks></LoginNetworkMasks>
			      <AllowUserToChangePassword>true</AllowUserToChangePassword>
			      <EnableSaveMFATicket>false</EnableSaveMFATicket>
		    </LoginProfilePreference>
		    <AccessKeyPreference>
			      <AllowUserToManageAccessKeys>false</AllowUserToManageAccessKeys>
		    </AccessKeyPreference>
		    <MFAPreference>
			      <AllowUserToManageMFADevices>true</AllowUserToManageMFADevices>
		    </MFAPreference>
	  </SecurityPreference>
	  <RequestId>30C9068D-FBAA-4998-9986-8A562FED0BC3</RequestId>
</GetSecurityPreferenceResponse>
```

`JSON` 格式

```
{
  "SecurityPreference": {
    "LoginProfilePreference": {
      "LoginSessionDuration": 6,
      "LoginNetworkMasks": "",
      "AllowUserToChangePassword": true,
      "EnableSaveMFATicket": false
    },
    "AccessKeyPreference": {
      "AllowUserToManageAccessKeys": false
    },
    "MFAPreference": {
      "AllowUserToManageMFADevices": true
    }
  },
  "RequestId": "30C9068D-FBAA-4998-9986-8A562FED0BC3"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

