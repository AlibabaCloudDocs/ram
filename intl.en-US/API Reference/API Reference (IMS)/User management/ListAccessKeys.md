# ListAccessKeys

Queries the AccessKey pairs of an Alibaba Cloud account or a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListAccessKeys&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListAccessKeys|The operation that you want to perform. Set the value to ListAccessKeys. |
|UserPrincipalName|String|No|test@example.onaliyun.com|The logon name of the RAM user.

 If this parameter is empty, the AccessKey pairs of the current user are queried. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|AccessKeys|Array of AccessKey| |The list of AccessKey pairs. |
|AccessKey| | | |
|AccessKeyId|String|0wNEpMMlzy7s\*\*\*\*|The AccessKey ID. |
|CreateDate|String|2020-10-13T12:33:18Z|The time when the AccessKey pair was created. |
|Status|String|Active|The status of the AccessKey pair. Valid values:

 -   Active
-   Inactive |
|UpdateDate|String|2020-10-13T12:33:18Z|The time when the AccessKey pair was updated. |
|RequestId|String|4B450CA1-36E8-4AA2-8461-86B42BF4CC4E|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListAccessKeys
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListAccessKeysResponse>
	  <RequestId>4B450CA1-36E8-4AA2-8461-86B42BF4CC4E</RequestId>
	  <AccessKeys>
		    <AccessKey>
			      <AccessKeyId>0wNEpMMlzy7s****</AccessKeyId>
			      <Status>Active</Status>
			      <CreateDate>2020-10-13T12:33:18Z</CreateDate>
			      <UpdateDate>2020-10-13T12:33:18Z</UpdateDate>
		    </AccessKey>
		    <AccessKey>
			      <AccessKeyId>WnIWUruvfaDT****</AccessKeyId>
			      <Status>Inactive</Status>
			      <CreateDate>2020-10-14T12:33:18Z</CreateDate>
			      <UpdateDate>2020-10-14T21:12:21Z</UpdateDate>
		    </AccessKey>
	  </AccessKeys>
</ListAccessKeysResponse>
```

`JSON` format

```
{
  "RequestId" : "4B450CA1-36E8-4AA2-8461-86B42BF4CC4E",
  "AccessKeys":{
    "AccessKey":[
      {
        "AccessKeyId": "0wNEpMMlzy7s****",
        "Status": "Active",
        "CreateDate": "2020-10-13T12:33:18Z",
        "UpdateDate": "2020-10-13T12:33:18Z"
      },
      {
        "AccessKeyId": "WnIWUruvfaDT****",
        "Status": "Inactive",
        "CreateDate": "2020-10-14T12:33:18Z",
        "UpdateDate": "2020-10-14T21:12:21Z"
      }
    ]
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

