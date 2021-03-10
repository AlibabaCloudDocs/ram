# API概览

访问控制提供以下相关API接口。

**说明：** [OpenAPI开发者门户](https://next.api.aliyun.com/product/Ram)提供在线调试API的功能，能显著降低API的使用难度，推荐您使用。

## 用户管理接口

|API|描述|
|---|--|
|[CreateUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateUser.md)|调用CreateUser接口创建RAM用户。|
|[GetUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/GetUser.md)|调用GetUser接口获取用户的详细信息。|
|[UpdateUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/UpdateUser.md)|调用UpdateUser接口更新用户的基本信息。|
|[DeleteUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/DeleteUser.md)|调用DeleteUser接口删除一个RAM用户。|
|[ListUsers](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/ListUsers.md)|调用ListUsers接口列出所有RAM用户。|
|[CreateLoginProfile](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateLoginProfile.md)|调用CreateLoginProfile接口为一个RAM用户启用Web控制台登录。|
|[GetLoginProfile](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/GetLoginProfile.md)|调用GetLoginProfile接口查看一个RAM用户的登录配置。|
|[DeleteLoginProfile](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/DeleteLoginProfile.md)|调用DeleteLoginProfile接口关闭指定RAM用户登录Web控制台的功能。|
|[UpdateLoginProfile](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/UpdateLoginProfile.md)|调用UpdateLoginProfile接口修改用户的登录配置。|
|[CreateAccessKey](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateAccessKey.md)|调用CreateAccessKey接口为RAM用户创建访问密钥。|
|[UpdateAccessKey](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/UpdateAccessKey.md)|调用UpdateAccessKey接口更新RAM用户访问密钥的状态。|
|[DeleteAccessKey](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/DeleteAccessKey.md)|调用DeleteAccessKey接口删除RAM用户的访问密钥。|
|[ListAccessKeys](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/ListAccessKeys.md)|调用ListAccessKeys接口列出指定用户的访问密钥。|
|[CreateVirtualMFADevice](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateVirtualMFADevice.md)|调用CreateVirtualMFADevice接口创建多因素认证设备。|
|[ListVirtualMFADevices](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/ListVirtualMFADevices.md)|调用ListVirtualMFADevices接口列出多因素认证设备。|
|[DeleteVirtualMFADevice](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/DeleteVirtualMFADevice.md)|调用DeleteVirtualMFADevice接口删除多因素认证设备。|
|[BindMFADevice](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/BindMFADevice.md)|调用BindMFADevice接口绑定多因素认证设备。|
|[UnbindMFADevice](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/UnbindMFADevice.md)|调用UnbindMFADevice接口解绑多因素认证设备。|
|[GetUserMFAInfo](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/GetUserMFAInfo.md)|调用GetUserMFAInfo接口获取指定RAM用户的多因素认证设备信息。|
|[ChangePassword](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/ChangePassword.md)|调用ChangePassword接口修改RAM用户密码。|

## 组管理接口

|API|描述|
|---|--|
|[CreateGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/CreateGroup.md)|调用CreateGroup接口创建用户组。|
|[GetGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/GetGroup.md)|调用GetGroup接口获取用户组信息。|
|[UpdateGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/UpdateGroup.md)|调用UpdateGroup接口更新用户组信息。|
|[ListGroups](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/ListGroups.md)|调用ListGroups接口列出所有的用户组。|
|[DeleteGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/DeleteGroup.md)|调用DeleteGroup接口删除指定的用户组。|
|[AddUserToGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/AddUserToGroup.md)|调用AddUserToGroup接口将RAM用户添加到指定的用户组。|
|[RemoveUserFromGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/RemoveUserFromGroup.md)|调用RemoveUserFromGroup接口将RAM用户从用户组中移除。|
|[ListGroupsForUser](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/ListGroupsForUser.md)|调用ListGroupsForUser接口列出指定RAM用户所加入的用户组信息。|
|[ListUsersForGroup](/intl.zh-CN/API参考/API参考（RAM）/组管理接口/ListUsersForGroup.md)|调用ListUsersForGroup接口列出指定用户组所包含的RAM用户。|

## 角色管理接口

|API|描述|
|---|--|
|[CreateRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/CreateRole.md)|调用CreateRole接口创建角色。|
|[GetRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/GetRole.md)|调用GetRole接口获取角色信息。|
|[UpdateRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/UpdateRole.md)|调用UpdateRole接口更新角色信息。|
|[ListRoles](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/ListRoles.md)|调用ListRoles接口列出角色。|
|[DeleteRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/DeleteRole.md)|调用DeleteRole接口删除指定的角色。|

## 权限策略管理接口

|API|描述|
|---|--|
|[CreatePolicy](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/CreatePolicy.md)|调用CreatePolicy接口创建一个权限策略。|
|[GetPolicy](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/GetPolicy.md)|调用GetPolicy接口获取指定的权限策略信息。|
|[DeletePolicy](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/DeletePolicy.md)|调用DeletePolicy接口删除指定的权限策略。|
|[ListPolicies](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListPolicies.md)|调用ListPolicies接口列出权限策略。|
|[CreatePolicyVersion](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/CreatePolicyVersion.md)|调用CreatePolicyVersion接口为权限策略创建新的版本。|
|[GetPolicyVersion](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/GetPolicyVersion.md)|调用GetPolicyVersion接口获取某个权限策略的版本。|
|[DeletePolicyVersion](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/DeletePolicyVersion.md)|调用DeletePolicyVersion接口删除指定的权限策略的某个版本。|
|[ListPolicyVersions](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListPolicyVersions.md)|调用ListPolicyVersions接口列出权限策略版本。|
|[SetDefaultPolicyVersion](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/SetDefaultPolicyVersion.md)|调用SetDefaultPolicyVersion接口设置权限策略默认版本。|
|[AttachPolicyToUser](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/AttachPolicyToUser.md)|调用AttachPolicyToUser接口为指定用户添加权限。|
|[DetachPolicyFromUser](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/DetachPolicyFromUser.md)|调用DetachPolicyFromUser接口为用户撤销指定的权限。|
|[AttachPolicyToGroup](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/AttachPolicyToGroup.md)|调用AttachPolicyToGroup接口为指定用户组添加权限。|
|[DetachPolicyFromGroup](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/DetachPolicyFromGroup.md)|调用DetachPolicyFromGroup接口为用户组撤销指定的权限。|
|[AttachPolicyToRole](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/AttachPolicyToRole.md)|调用AttachPolicyToRole接口为指定角色添加权限。|
|[DetachPolicyFromRole](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/DetachPolicyFromRole.md)|调用DetachPolicyFromRole接口为角色撤销指定的权限。|
|[ListEntitiesForPolicy](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListEntitiesForPolicy.md)|调用ListEntitiesForPolicy接口列出引用权限策略的实体。|
|[ListPoliciesForUser](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListPoliciesForUser.md)|调用ListPoliciesForUser接口列出指定用户的权限策略。|
|[ListPoliciesForGroup](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListPoliciesForGroup.md)|调用ListPoliciesForGroup接口列出用户组的权限策略。|
|[ListPoliciesForRole](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/ListPoliciesForRole.md)|调用ListPoliciesForRole接口列出角色的权限策略。|

## 安全设置接口

|API|描述|
|---|--|
|[SetAccountAlias](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/SetAccountAlias.md)|调用SetAccountAlias接口设置云账号别名。|
|[GetAccountAlias](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/GetAccountAlias.md)|调用GetAccountAlias接口查看云账号别名。|
|[ClearAccountAlias](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/ClearAccountAlias.md)|调用ClearAccountAlias接口清除云账号别名。|
|[SetPasswordPolicy](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/SetPasswordPolicy.md)|调用SetPasswordPolicy接口设置RAM用户密码强度等策略信息。|
|[GetPasswordPolicy](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/GetPasswordPolicy.md)|调用GetPasswordPolicy接口获取RAM用户密码强度等策略信息。|
|[SetSecurityPreference](/intl.zh-CN/API参考/API参考（RAM）/安全设置接口/SetSecurityPreference.md)|调用SetSecurityPreference接口设置全局安全首选项。|

