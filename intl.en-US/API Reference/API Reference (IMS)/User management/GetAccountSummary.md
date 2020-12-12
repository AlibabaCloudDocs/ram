# GetAccountSummary

Queries the overview information of an Alibaba Cloud account.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetAccountSummary&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetAccountSummary|The operation that you want to perform. Set the value to GetAccountSummary. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|81313F5E-3C85-478F-BCC9-E1B70E4556DB|The ID of the request. |
|SummaryMap|Struct| |The overview information of the Alibaba Cloud account. |
|AccessKeysPerUserQuota|Integer|2|The maximum number of AccessKey pairs that a RAM user can have. |
|AttachedPoliciesPerGroupQuota|Integer|5|The maximum number of custom policies that can be added to a RAM user group. |
|AttachedPoliciesPerRoleQuota|Integer|5|The maximum number of custom policies that can be added to a RAM role. |
|AttachedPoliciesPerUserQuota|Integer|10|The maximum number of custom policies that can be added to a RAM user. |
|AttachedSystemPoliciesPerGroupQuota|Integer|20|The maximum number of system policies that can be added to a RAM user group. |
|AttachedSystemPoliciesPerRoleQuota|Integer|20|The maximum number of system policies that can be added to a RAM role. |
|AttachedSystemPoliciesPerUserQuota|Integer|20|The maximum number of system policies that can be added to a RAM user. |
|Groups|Integer|7|The number of RAM user groups. |
|GroupsPerUserQuota|Integer|5|The maximum number of RAM user groups to which a RAM user can be added. |
|GroupsQuota|Integer|50|The maximum number of RAM user groups that can be created. |
|MFADevices|Integer|13|The number of virtual multi-factor authentication \(MFA\) devices. |
|MFADevicesInUse|Integer|2|The number of virtual MFA devices in use. |
|Policies|Integer|13|The number of custom policies. |
|PoliciesQuota|Integer|1500|The maximum number of custom policies that can be created. |
|PolicySizeQuota|Integer|2048|The maximum length of the policy content. |
|Roles|Integer|19|The number of RAM roles. |
|RolesQuota|Integer|1000|The maximum number of RAM roles that can be created. |
|Users|Integer|9|The number of RAM users. |
|UsersQuota|Integer|1000|The maximum number of RAM users that can be created. |
|VersionsPerPolicyQuota|Integer|5|The maximum number of policy versions. |
|VirtualMFADevicesQuota|Integer|1000|The maximum number of virtual MFA devices that can be created. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetAccountSummary
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetAccountSummaryResponse>
	  <RequestId>81313F5E-3C85-478F-BCC9-E1B70E4556DB</RequestId>
	  <SummaryMap>
		    <Policies>13</Policies>
		    <GroupsPerUserQuota>5</GroupsPerUserQuota>
		    <AttachedPoliciesPerUserQuota>10</AttachedPoliciesPerUserQuota>
		    <Roles>19</Roles>
		    <Users>9</Users>
		    <RolesQuota>1000</RolesQuota>
		    <PoliciesQuota>1500</PoliciesQuota>
		    <VirtualMFADevicesQuota>1000</VirtualMFADevicesQuota>
		    <AttachedSystemPoliciesPerGroupQuota>20</AttachedSystemPoliciesPerGroupQuota>
		    <MFADevicesInUse>2</MFADevicesInUse>
		    <AccessKeysPerUserQuota>2</AccessKeysPerUserQuota>
		    <VersionsPerPolicyQuota>5</VersionsPerPolicyQuota>
		    <PolicySizeQuota>2048</PolicySizeQuota>
		    <AttachedPoliciesPerGroupQuota>5</AttachedPoliciesPerGroupQuota>
		    <AttachedSystemPoliciesPerUserQuota>20</AttachedSystemPoliciesPerUserQuota>
		    <Groups>7</Groups>
		    <AttachedPoliciesPerRoleQuota>5</AttachedPoliciesPerRoleQuota>
		    <UsersQuota>1000</UsersQuota>
		    <AttachedSystemPoliciesPerRoleQuota>20</AttachedSystemPoliciesPerRoleQuota>
		    <MFADevices>13</MFADevices>
		    <GroupsQuota>50</GroupsQuota>
	  </SummaryMap>
</GetAccountSummaryResponse>
```

`JSON` format

```
{
  "RequestId": "81313F5E-3C85-478F-BCC9-E1B70E4556DB",
  "SummaryMap": {
    "Policies": 13,
    "GroupsPerUserQuota": 5,
    "AttachedPoliciesPerUserQuota": 10,
    "Roles": 19,
    "Users": 9,
    "RolesQuota": 1000,
    "PoliciesQuota": 1500,
    "VirtualMFADevicesQuota": 1000,
    "AttachedSystemPoliciesPerGroupQuota": 20,
    "MFADevicesInUse": 2,
    "AccessKeysPerUserQuota": 2,
    "VersionsPerPolicyQuota": 5,
    "PolicySizeQuota": 2048,
    "AttachedPoliciesPerGroupQuota": 5,
    "AttachedSystemPoliciesPerUserQuota": 20,
    "Groups": 7,
    "AttachedPoliciesPerRoleQuota": 5,
    "UsersQuota": 1000,
    "AttachedSystemPoliciesPerRoleQuota": 20,
    "MFADevices": 13,
    "GroupsQuota": 50
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

