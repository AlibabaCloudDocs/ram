# UpdateGroup

Modifies the information of a RAM user group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=UpdateGroup&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateGroup|The operation that you want to perform. Set the value to UpdateGroup. |
|GroupName|String|Yes|Dev-Team|The name of the RAM user group. |
|NewGroupName|String|No|Test-Team|The new name of the RAM user group.

 The name can be up to 64 characters in length and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). |
|NewDisplayName|String|No|Test-Team|The new display name of the RAM user group.

 The name can be up to 24 characters in length. |
|NewComments|String|No|Test team|The new description.

 The value can be up to 128 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Group|Struct| |The information of the RAM user group. |
|Comments|String|Test team|The description. |
|CreateDate|String|2020-10-19T16:15:17Z|The creation time. |
|DisplayName|String|Test-Team|The display name of the RAM user group. |
|GroupId|String|740317625433843\*\*\*\*|The ID of the RAM user group. |
|GroupName|String|Test-Team|The name of the RAM user group. |
|UpdateDate|String|2020-10-20T03:44:27Z|The update time. |
|RequestId|String|CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=UpdateGroup
&GroupName=Dev-Team
&NewGroupName=Test-Team
&NewDisplayName=Test-Team
&Newcomments=Test team
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UpdateGroupResponse>
	  <Group>
		    <GroupName>Test-Team</GroupName>
		    <UpdateDate>2020-10-20T03:44:27Z</UpdateDate>
		    <Comments>Test team</Comments>
            <GroupId>740317625433843****</GroupId>
		    <DisplayName>Test-Team</DisplayName>
		    <CreateDate>2020-10-19T16:15:17Z</CreateDate>
	  </Group>
	  <RequestId>CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287</RequestId>
</UpdateGroupResponse>
```

`JSON` format

```
{
  "Group": {
    "GroupName": "Test-Team",
    "UpdateDate": "2020-10-20T03:44:27Z",
    "Comments": "Test team",
    "GroupId": "740317625433843****",
    "DisplayName": "Test-Team",
    "CreateDate": "2020-10-19T16:15:17Z"
  },
  "RequestId": "CDA656E3-3CE9-4A03-A8A3-B42A0C3C3287"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

