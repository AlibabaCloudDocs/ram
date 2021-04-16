# List of operations by function

The following tables list the API operations that are available for use in Resource Access Management \(RAM\).

**Note:** Alibaba Cloud provides [OpenAPI Developer Portal](https://next.api.aliyun.com/product/Ram) to simplify API usage. You can use OpenAPI Explorer to debug API operations.

## RAM user management

|API|Description|
|---|-----------|
|CreateUser|Creates a RAM user.|
|GetUser|Queries the information of a RAM user.|
|UpdateUser|Modifies a RAM user.|
|DeleteUser|Deletes a RAM user.|
|ListUsers|Queries the list of all RAM users.|
|CreateLoginProfile|Enables console logon for a RAM user.|
|GetLoginProfile|Queries the logon configurations of a RAM user.|
|DeleteLoginProfile|Disables console logon for a RAM user.|
|UpdateLoginProfile|Modifies the logon configurations of a RAM user.|
|CreateAccessKey|Creates an AccessKey pair for a RAM user.|
|UpdateAccessKey|Changes the status of an AccessKey pair that belongs to a RAM user.|
|DeleteAccessKey|Deletes an AccessKey pair of a RAM user.|
|ListAccessKeys|Queries the list of all AccessKey pairs that belong to a RAM user.|
|CreateVirtualMFADevice|Creates a multi-factor authentication \(MFA\) device.|
|ListVirtualMFADevices|Queries the list of all MFA devices.|
|DeleteVirtualMFADevice|Deletes an MFA device.|
|BindMFADevice|Attaches an MFA device to a RAM user.|
|UnbindMFADevice|Detaches an MFA device from a RAM user.|
|GetUserMFAInfo|Queries the MFA device that is attached to a RAM user.|
|ChangePassword|Changes the password of a RAM user.|

## Management of RAM user groups

|API|Description|
|---|-----------|
|CreateGroup|Creates a RAM user group.|
|GetGroup|Queries the information of a RAM user group.|
|UpdateGroup|Modifies a RAM user group.|
|ListGroups|Queries the list of all RAM user groups.|
|DeleteGroup|Deletes a RAM user group.|
|AddUserToGroup|Adds a RAM user to a RAM user group.|
|RemoveUserFromGroup|Removes a RAM user from a RAM user group.|
|ListGroupsForUser|Queries the RAM user groups to which a RAM user belongs.|
|ListUsersForGroup|Queries RAM users in a RAM user group.|

## RAM role management

|API|Description|
|---|-----------|
|CreateRole|Creates a RAM role.|
|GetRole|Queries the information of a RAM role.|
|UpdateRole|Modifies a RAM role.|
|ListRoles|Queries the list of all RAM roles.|
|DeleteRole|Deletes a RAM role.|

## Policy management

|API|Description|
|---|-----------|
|CreatePolicy|Creates a policy.|
|GetPolicy|Queries the information of a policy.|
|DeletePolicy|Deletes a policy.|
|ListPolicies|Queries a list of policies.|
|CreatePolicyVersion|Creates a version for an existing policy.|
|GetPolicyVersion|Queries the information of a policy version.|
|DeletePolicyVersion|Deletes a policy version.|
|ListPolicyVersions|Queries the versions of a policy.|
|SetDefaultPolicyVersion|Sets the default version for a policy.|
|AttachPolicyToUser|Attaches a policy to a RAM user.|
|DetachPolicyFromUser|Detaches a policy from a RAM user.|
|AttachPolicyToGroup|Attaches a policy to a RAM user group.|
|DetachPolicyFromGroup|Detaches a policy from a RAM user group.|
|AttachPolicyToRole|Attaches a policy to a RAM role.|
|DetachPolicyFromRole|Detaches a policy from a RAM role.|
|ListEntitiesForPolicy|Queries the entities to which a policy is attached.|
|ListPoliciesForUser|Queries the policies that are attached to a RAM user.|
|ListPoliciesForGroup|Queries the policies that are attached to a RAM user group.|
|ListPoliciesForRole|Queries the policies that are attached to a RAM role.|

## Security control

|API|Description|
|---|-----------|
|SetAccountAlias|Sets the alias of an Alibaba Cloud account.|
|GetAccountAlias|Queries the alias of an Alibaba Cloud account.|
|ClearAccountAlias|Deletes the alias of an Alibaba Cloud account.|
|SetPasswordPolicy|Sets the password policy for RAM users, including the password strength.|
|GetPasswordPolicy|Queries the password policy of RAM users, including the password strength.|
|SetSecurityPreference|Sets the security preferences.|

