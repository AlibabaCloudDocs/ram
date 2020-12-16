# SetSecurityPreference

调用SetSecurityPreference设置RAM用户的全局安全首选项。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=SetSecurityPreference&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetSecurityPreference|要执行的操作。取值：SetSecurityPreference。 |
|EnableSaveMFATicket|Boolean|否|false|是否允许RAM用户在登录时保存多因素设备认证状态，有效期为7天。取值：

 -   true：允许。
-   false（默认值）：不允许。 |
|AllowUserToChangePassword|Boolean|否|true|是否允许RAM用户自主管理密码。取值：

 -   true（默认值）：允许。
-   false：不允许。 |
|AllowUserToManageAccessKeys|Boolean|否|false|是否允许RAM用户自主管理访问密钥。取值：

 -   true：允许。
-   false（默认值）：不允许。 |
|AllowUserToManageMFADevices|Boolean|否|true|是否允许RAM用户自主管理多因素认证设备。取值：

 -   true（默认值）：允许。
-   false：不允许。 |
|LoginSessionDuration|Integer|否|6|RAM用户登录有效期。

 取值范围：6~24。单位：小时。

 默认值：6。 |
|LoginNetworkMasks|String|否|10.0.0.0/8|登录掩码。登录掩码决定哪些IP地址会受到登录控制台的影响，包括密码登录和单点登录（SSO），但使用访问密钥发起的API调用并不受影响。

 -   如果指定掩码，RAM用户只能从指定的IP地址进行登录。
-   如果不指定任何掩码，登录控制台功能将适用于整个网络。

 当需要配置多个登录掩码时，请使用分号（;）来分隔，例如：192.168.0.0/16;10.0.0.0/8。

 最多配置25个登录掩码，总长度最大512个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|17494710-B4BA-4185-BBBB-C1A6ABDE1639|请求ID。 |
|SecurityPreference|Struct| |安全首选项信息。 |
|AccessKeyPreference|Struct| |访问密钥首选项。 |
|AllowUserToManageAccessKeys|Boolean|false|是否允许RAM用户自主管理访问密钥。 |
|LoginProfilePreference|Struct| |登录首选项。 |
|AllowUserToChangePassword|Boolean|true|是否允许RAM用户自主管理密码。 |
|EnableSaveMFATicket|Boolean|false|是否允许RAM用户在登录时保存多因素设备认证状态。如果允许（true），则7天内不用验证MFA。 |
|LoginNetworkMasks|String|10.0.0.0/8|登录掩码。 |
|LoginSessionDuration|Integer|6|RAM用户登录有效期。 |
|MFAPreference|Struct| |多因素认证首选项。 |
|AllowUserToManageMFADevices|Boolean|false|是否允许RAM用户自主管理多因素认证设备。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=SetSecurityPreference
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetSecurityPreferenceResponse>
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
	  <RequestId>17494710-B4BA-4185-BBBB-C1A6ABDE1639</RequestId>
</SetSecurityPreferenceResponse>
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
  "RequestId": "17494710-B4BA-4185-BBBB-C1A6ABDE1639"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

