# GetAccountSecurityPracticeReport

调用GetAccountSecurityPracticeReport查询阿里云账号的安全报告。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetAccountSecurityPracticeReport&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAccountSecurityPracticeReport|要执行的操作。取值：GetAccountSecurityPracticeReport。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AccountSecurityPracticeInfo|Struct| |阿里云账号安全报告信息。 |
|AccountSecurityPracticeUserInfo|Struct| |阿里云账号安全报告信息。 |
|BindMfa|Boolean|false|是否已开启多因素认证。取值：

 -   true：已开启。
-   false：未开启。 |
|OldAkNum|Integer|0|阿里云账号中旧访问密钥的个数。 |
|RootWithAccessKey|Integer|1|阿里云账号访问密钥（AccessKey）的个数。 |
|SubUser|Integer|9|阿里云账号中RAM用户的个数。 |
|SubUserBindMfa|Integer|0|绑定了多因素认证设备的RAM用户的个数。 |
|SubUserPwdLevel|String|low|RAM用户密码强度的等级。取值：

 -   low
-   mid
-   high |
|SubUserWithOldAccessKey|Integer|0|使用旧访问密钥的RAM用户的个数。 |
|SubUserWithUnusedAccessKey|Integer|0|拥有未使用访问密钥的RAM用户的个数。 |
|UnusedAkNum|Integer|0|阿里云账号中未使用的访问密钥的个数。 |
|Score|Integer|63|阿里云账号安全最终得分。 |
|RequestId|String|ABA822EE-85C2-4418-9577-A1831FC8466D|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetAccountSecurityPracticeReport
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetAccountSecurityPracticeReportResponse>
	  <RequestId>ABA822EE-85C2-4418-9577-A1831FC8466D</RequestId>
	  <AccountSecurityPracticeInfo>
		    <Score>63</Score>
		    <AccountSecurityPracticeUserInfo>
			      <SubUser>9</SubUser>
			      <SubUserBindMfa>0</SubUserBindMfa>
			      <SubUserWithUnusedAccessKey>0</SubUserWithUnusedAccessKey>
			      <RootWithAccessKey>1</RootWithAccessKey>
			      <SubUserWithOldAccessKey>0</SubUserWithOldAccessKey>
			      <SubUserPwdLevel>low</SubUserPwdLevel>
			      <UnusedAkNum>0</UnusedAkNum>
			      <OldAkNum>0</OldAkNum>
			      <BindMfa>false</BindMfa>
		    </AccountSecurityPracticeUserInfo>
	  </AccountSecurityPracticeInfo>
</GetAccountSecurityPracticeReportResponse>
```

`JSON` 格式

```
{
  "RequestId": "ABA822EE-85C2-4418-9577-A1831FC8466D",
  "AccountSecurityPracticeInfo": {
    "Score": 63,
    "AccountSecurityPracticeUserInfo": {
      "SubUser": 9,
      "SubUserBindMfa": 0,
      "SubUserWithUnusedAccessKey": 0,
      "RootWithAccessKey": 1,
      "SubUserWithOldAccessKey": 0,
      "SubUserPwdLevel": "low",
      "UnusedAkNum": 0,
      "OldAkNum": 0,
      "BindMfa": false
    }
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

