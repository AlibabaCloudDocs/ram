# GetAccountSummary

调用GetAccountSummary查询阿里云账号（主账号）的概览信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetAccountSummary&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetAccountSummary|要执行的操作。取值：GetAccountSummary。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|81313F5E-3C85-478F-BCC9-E1B70E4556DB|请求ID。 |
|SummaryMap|Struct| |阿里云账号概览信息。 |
|AccessKeysPerUserQuota|Integer|2|每个RAM用户允许拥有访问密钥的最大数量。 |
|AttachedPoliciesPerGroupQuota|Integer|5|每个用户组允许添加自定义策略的最大数量。 |
|AttachedPoliciesPerRoleQuota|Integer|5|每个RAM角色允许添加自定义策略的最大数量。 |
|AttachedPoliciesPerUserQuota|Integer|10|每个RAM用户允许添加自定义策略的最大数量。 |
|AttachedSystemPoliciesPerGroupQuota|Integer|20|每个用户组允许添加系统策略的最大数量。 |
|AttachedSystemPoliciesPerRoleQuota|Integer|20|每个RAM角色允许添加系统策略的最大数量。 |
|AttachedSystemPoliciesPerUserQuota|Integer|20|每个RAM用户允许添加系统策略的最大数量。 |
|Groups|Integer|7|用户组数量。 |
|GroupsPerUserQuota|Integer|5|每个RAM用户允许加入的用户组最大数量。 |
|GroupsQuota|Integer|50|允许创建用户组的最大数量。 |
|MFADevices|Integer|13|虚拟多因素认证设备的数量。 |
|MFADevicesInUse|Integer|2|使用中的虚拟多因素认证设备的数量。 |
|Policies|Integer|13|自定义策略数量。 |
|PoliciesQuota|Integer|1500|允许创建自定义策略的最大数量。 |
|PolicySizeQuota|Integer|2048|权限策略内容的最大长度。 |
|Roles|Integer|19|RAM角色数量。 |
|RolesQuota|Integer|1000|允许创建RAM角色的最大数量。 |
|Users|Integer|9|RAM用户数量。 |
|UsersQuota|Integer|1000|允许创建RAM用户的最大数量。 |
|VersionsPerPolicyQuota|Integer|5|权限策略版本的最大数量。 |
|VirtualMFADevicesQuota|Integer|1000|允许创建虚拟多因素认证设备的最大数量。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetAccountSummary
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

