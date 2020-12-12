# ChangePassword

Changes the password that is used to log on to the console.

**Note:** This operation is available only for RAM users. Before you call this operation, make sure that `AllowUserToChangePassword` in [SetSecurityPreference](~~43765~~) is set to `True`. The value True indicates that RAM users can change their passwords.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ChangePassword&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ChangePassword|The operation that you want to perform. Set the value to ChangePassword. |
|OldPassword|String|Yes|mypassword|The old password that is used to log on to the console. |
|NewPassword|String|Yes|newpassword|The new password that is used to log on to the console.

 The password must meet the complexity requirements. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ChangePassword
&OldPassword=mypassword
&NewPassword=newpassword
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ChangePasswordResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ChangePasswordResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

