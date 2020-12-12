# GetGroup

Queries the information of a RAM user group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetGroup&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetGroup|The operation that you want to perform. Set the value to GetGroup. |
|GroupName|String|Yes|Dev-Team|The name of the RAM user group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Group|Struct| |The information of the RAM user group. |
|Comments|String|Development team|The description. |
|CreateDate|String|2020-10-19T16:15:17Z|The creation time. |
|DisplayName|String|Dev-Team|The display name of the RAM user group. |
|GroupId|String|740317625433843\*\*\*\*|The ID of the RAM user group. |
|GroupName|String|Dev-Team|The name of the RAM user group. |
|UpdateDate|String|2020-10-19T16:15:17Z|The update time. |
|RequestId|String|86ECEC3C-7262-4C3C-94B4-A98F7CC1F060|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetGroup
&GroupName=Dev-Team
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetGroupResponse>
	  <Group>
		    <GroupName>Dev-Team</GroupName>
		    <UpdateDate>2020-10-19T16:15:17Z</UpdateDate>
		    <Comments>Development team</Comments>
            <GroupId>740317625433843****</GroupId>
		    <DisplayName>Dev-Team</DisplayName>
		    <CreateDate>2020-10-19T16:15:17Z</CreateDate>
	  </Group>
	  <RequestId>86ECEC3C-7262-4C3C-94B4-A98F7CC1F060</RequestId>
</GetGroupResponse>
```

`JSON` format

```
{
  "Group": {
    "GroupName": "Dev-Team",
    "UpdateDate": "2020-10-19T16:15:17Z",
    "Comments": "Development team",
    "GroupId": "740317625433843****",
    "DisplayName": "Dev-Team",
    "CreateDate": "2020-10-19T16:15:17Z"
  },
  "RequestId": "86ECEC3C-7262-4C3C-94B4-A98F7CC1F060"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

