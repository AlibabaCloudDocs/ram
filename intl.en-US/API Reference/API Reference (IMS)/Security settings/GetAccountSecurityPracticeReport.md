# GetAccountSecurityPracticeReport

Queries the security report for an Alibaba Cloud account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetAccountSecurityPracticeReport&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetAccountSecurityPracticeReport|The operation that you want to perform. Set the value to GetAccountSecurityPracticeReport. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AccountSecurityPracticeInfo|Struct| |The information of the security report for the Alibaba Cloud account. |
|AccountSecurityPracticeUserInfo|Struct| |The information of the security report for the Alibaba Cloud account. |
|BindMfa|Boolean|false|Indicates whether MFA is enabled. Valid values:

 -   true
-   false |
|OldAkNum|Integer|0|The number of old AccessKey pairs for the Alibaba Cloud account. |
|RootWithAccessKey|Integer|1|The number of AccessKey pairs for the Alibaba Cloud account. |
|SubUser|Integer|9|The number of RAM users within the Alibaba Cloud account. |
|SubUserBindMfa|Integer|0|The number of RAM users that have MFA devices bound. |
|SubUserPwdLevel|String|low|The complexity level of the password for the RAM user. Valid values:

 -   low
-   mid
-   high |
|SubUserWithOldAccessKey|Integer|0|The number of RAM users that use the old AccessKey pairs. |
|SubUserWithUnusedAccessKey|Integer|0|The number of RAM users that have no AccessKey pairs. |
|UnusedAkNum|Integer|0|The number of AccessKey pairs that are not used for the Alibaba Cloud account. |
|Score|Integer|63|The security score of the Alibaba Cloud account. |
|RequestId|String|ABA822EE-85C2-4418-9577-A1831FC8466D|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetAccountSecurityPracticeReport
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

