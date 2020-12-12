# ListGroupsForUser

Queries the RAM user groups to which a RAM user belongs.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListGroupsForUser&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListGroupsForUser|The operation that you want to perform. Set the value to ListGroupsForUser. |
|UserPrincipalName|String|Yes|test@example.onaliyun.com|The logon name of the RAM user. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Groups|Array of Group| |The information of the RAM user groups. |
|Group| | | |
|Comments|String|Test team|The description. |
|DisplayName|String|Test-Team|The display name of the RAM user group. |
|GroupId|String|740317625433843\*\*\*\*|The ID of the RAM user group. |
|GroupName|String|Test-Team|The name of the RAM user group. |
|JoinDate|String|2020-10-20T06:57:00Z|The time when the RAM user was added. |
|RequestId|String|7158A935-FB5E-49A7-8E52-FDA5B2B67247|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListGroupsForUser
&UserPrincipalName=test@example.onaliyun.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListGroupsForUserResponse>
      <RequestId>7158A935-FB5E-49A7-8E52-FDA5B2B67247</RequestId>
      <Groups>
            <Group>
                  <GroupName>Test-Team</GroupName>
                  <Comments>Test team</Comments>
                  <GroupId>740317625433843****</GroupId>
                  <DisplayName>Test-Team</DisplayName>
                  <JoinDate>2020-10-20T06:57:00Z</JoinDate>
            </Group>
      </Groups>
</ListGroupsForUserResponse>
```

`JSON` format

```
{
  "RequestId": "7158A935-FB5E-49A7-8E52-FDA5B2B67247",
  "Groups": {
    "Group": [
      {
        "GroupName": "Test-Team",
        "Comments":"Test team",
        "GroupId": "740317625433843****",
        "DisplayName": "Test-Team",
        "JoinDate": "2020-10-20T06:57:00Z"
      }
    ]
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

