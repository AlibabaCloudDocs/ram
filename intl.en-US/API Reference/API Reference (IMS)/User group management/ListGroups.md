# ListGroups

Queries RAM user groups.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListGroups&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListGroups|The operation that you want to perform. Set the value to ListGroups. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|100|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be `true`.

 Valid values: 1 to 100. Default value: 100. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Groups|Array of Group| |The information of the RAM user groups. |
|Group| | | |
|Comments|String|Development team|The description. |
|CreateDate|String|2020-10-19T12:33:18Z|The creation time. |
|DisplayName|String|Dev-Team|The display name of the RAM user group. |
|GroupId|String|740317625433843\*\*\*\*|The ID of the RAM user group. |
|GroupName|String|dev-team|The name of the RAM user group. |
|UpdateDate|String|2020-10-19T12:33:18Z|The update time. |
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

 -   true
-   false |
|Marker|String|EXAMPLE|The `marker`. This parameter is returned only if the value of `IsTruncated` is `true`. If the parameter is returned, you can call this operation again and set this parameter to obtain the truncated part. |
|RequestId|String|065527AA-2F2E-AD7C-7484-F2626CFE4934|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListGroups
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListGroupsResponse>
	  <Groups>
		    <Group>
			      <Comments>Development team</Comments>
			      <CreateDate>2020-10-19T12:33:18Z</CreateDate>
			      <DisplayName>Dev-Team</DisplayName>
			      <GroupName>Dev-Team</GroupName>
                  <GroupId>740317625433843****</GroupId>
			      <UpdateDate>2020-10-19T12:33:18Z</UpdateDate>
		    </Group>
	  </Groups>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
	  <RequestId>065527AA-2F2E-AD7C-7484-F2626CFE4934</RequestId>
</ListGroupsResponse>
```

`JSON` format

```
{
  "Groups": {
    "Group": [
      {
        "Comments": "Development team",
        "CreateDate": "2020-10-19T12:33:18Z",
        "DisplayName": "Dev-Team",
        "GroupName": "Dev-Team",
        "GroupId": "740317625433843****",
        "UpdateDate": "2020-10-19T12:33:18Z"
      }
    ]
  },
  "IsTruncated": true,
  "Marker": "EXAMPLE",
  "RequestId": "065527AA-2F2E-AD7C-7484-F2626CFE4934"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

