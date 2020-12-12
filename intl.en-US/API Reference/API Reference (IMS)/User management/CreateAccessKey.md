# CreateAccessKey

Creates an AccessKey pair for an Alibaba Cloud account or a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=CreateAccessKey&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateAccessKey|The operation that you want to perform. Set the value to CreateAccessKey. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 If this parameter is empty, an AccessKey pair is created for the current user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AccessKey|Struct| |The information of the AccessKey pair. |
|AccessKeyId|String|LTAI4G3HaMmeHpay2gcq\*\*\*\*|The AccessKey ID provided to you by Alibaba Cloud. |
|AccessKeySecret|String|Y3MSLE6OgizS4qrz5LVFDoyZEL\*\*\*\*|The AccessKey secret provided to you by Alibaba Cloud. |
|CreateDate|String|2020-10-15T08:08:54Z|The time when the AccessKey pair was created. |
|Status|String|Active|The status of the AccessKey pair. Valid values:

 -   Active
-   Inactive |
|RequestId|String|19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=CreateAccessKey
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateAccessKeyResponse>
	  <RequestId>19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB</RequestId>
	  <AccessKey>
		    <Status>Active</Status>
		    <AccessKeyId>LTAI4G3HaMmeHpay2gcq****</AccessKeyId>
		    <AccessKeySecret>Y3MSLE6OgizS4qrz5LVFDoyZEL****</AccessKeySecret>
		    <CreateDate>2020-10-15T08:08:54Z</CreateDate>
	  </AccessKey>
</CreateAccessKeyResponse>
```

`JSON` format

```
{
  "RequestId": "19DDD9F7-AFCC-4D72-8CBA-CCE5A142E7AB",
  "AccessKey": {
    "Status": "Active",
    "AccessKeyId": "LTAI4G3HaMmeHpay2gcq****",
    "AccessKeySecret": "Y3MSLE6OgizS4qrz5LVFDoyZEL****",
    "CreateDate": "2020-10-15T08:08:54Z"
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

