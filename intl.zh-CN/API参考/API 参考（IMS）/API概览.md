# API概览

IMS（Identity Management Service）提供以下相关API。

## 用户管理API

|API|描述|
|---|--|
|[CreateUser](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/CreateUser.md)|调用CreateUser创建RAM用户。|
|[GetUser](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetUser.md)|调用GetUser查询RAM用户的详细信息。|
|[UpdateUser](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateUser.md)|调用UpdateUser修改RAM用户信息。|
|[DeleteUser](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteUser.md)|调用DeleteUser删除RAM用户。|
|[ListUsers](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ListUsers.md)|调用ListUsers查询所有RAM用户的详细信息。|
|[ListUserBasicInfos](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ListUserBasicInfos.md)|调用ListUserBasicInfos查询所有RAM用户的基本信息。|
|[CreateLoginProfile](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/CreateLoginProfile.md)|调用CreateLoginProfile开启指定RAM用户的控制台登录。|
|[GetLoginProfile](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetLoginProfile.md)|调用GetLoginProfile查询指定RAM用户的控制台登录信息。|
|[UpdateLoginProfile](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateLoginProfile.md)|调用UpdateLoginProfile修改指定RAM用户的控制台登录信息。|
|[DeleteLoginProfile](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteLoginProfile.md)|调用DeleteLoginProfile关闭指定RAM用户的控制台登录。|
|[ChangePassword](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ChangePassword.md)|RAM用户调用ChangePassword修改自己的控制台登录密码。|
|[CreateAccessKey](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/CreateAccessKey.md)|调用CreateAccessKey创建阿里云账号（主账号）或RAM用户的访问密钥。|
|[UpdateAccessKey](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateAccessKey.md)|调用UpdateAccessKey修改阿里云账号（主账号）或RAM用户的访问密钥状态。|
|[DeleteAccessKey](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteAccessKey.md)|调用DeleteAccessKey删除阿里云账号（主账号）或RAM用户的访问密钥。|
|[ListAccessKeys](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ListAccessKeys.md)|调用ListAccessKeys查询阿里云账号（主账号）或RAM用户的访问密钥列表。|
|[GetAccessKeyLastUsed](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccessKeyLastUsed.md)|调用GetAccessKeyLastUsed查询指定访问密钥的最后使用时间。|
|[CreateVirtualMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/CreateVirtualMFADevice.md)|调用CreateVirtualMFADevice创建多因素认证设备。|
|[ListVirtualMFADevices](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ListVirtualMFADevices.md)|调用ListVirtualMFADevices查询多因素认证设备列表。|
|[DeleteVirtualMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteVirtualMFADevice.md)|调用DeleteVirtualMFADevice删除多因素认证设备。|
|[DisableVirtualMFA](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DisableVirtualMFA.md)|调用DisableVirtualMFA解绑并删除指定RAM用户的多因素认证设备。|
|[BindMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/BindMFADevice.md)|调用BindMFADevice为RAM用户绑定多因素认证设备。|
|[UnbindMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/UnbindMFADevice.md)|调用UnbindMFADevice为RAM用户解绑多因素认证设备。|
|[GetAccountMFAInfo](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccountMFAInfo.md)|调用GetAccountMFAInfo查询阿里云账号（主账号）的多因素认证设备信息。|
|[GetUserMFAInfo](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetUserMFAInfo.md)|调用GetUserMFAInfo查询RAM用户绑定的多因素认证设备信息。|
|[GenerateCredentialReport](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GenerateCredentialReport.md)|调用GenerateCredentialReport生成用户凭证报告。|
|[GetCredentialReport](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GetCredentialReport.md)|调用GetCredentialReport查询用户凭证报告内容。|
|[GetAccountSecurityPracticeReport](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GetAccountSecurityPracticeReport.md)|调用GetAccountSecurityPracticeReport查询阿里云账号的安全报告。|
|[GetAccountSummary](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccountSummary.md)|调用GetAccountSummary查询阿里云账号（主账号）的概览信息。|

## 用户组管理API

|API|描述|
|---|--|
|[CreateGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/CreateGroup.md)|调用CreateGroup创建用户组。|
|[GetGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/GetGroup.md)|调用GetGroup查询指定用户组信息。|
|[UpdateGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/UpdateGroup.md)|调用UpdateGroup修改指定用户组的信息。|
|[DeleteGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/DeleteGroup.md)|调用DeleteGroup删除指定的用户组。|
|[ListGroups](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/ListGroups.md)|调用ListGroups查询用户组列表。|
|[AddUserToGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/AddUserToGroup.md)|调用AddUserToGroup将RAM用户添加到指定的用户组。|
|[ListUsersForGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/ListUsersForGroup.md)|调用ListUsersForGroup查询指定用户组内的RAM用户列表。|
|[ListGroupsForUser](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/ListGroupsForUser.md)|调用ListGroupsForUser查询指定RAM用户加入的用户组列表。|
|[RemoveUserFromGroup](/intl.zh-CN/API参考/API 参考（IMS）/用户组管理/RemoveUserFromGroup.md)|调用RemoveUserFromGroup将RAM用户从用户组中移除。|

## 单点登录（SSO）管理API

|API|描述|
|---|--|
|[SetUserSsoSettings](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/SetUserSsoSettings.md)|调用SetUserSsoSettings设置用户SSO身份提供商信息。|
|[GetUserSsoSettings](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/GetUserSsoSettings.md)|调用GetUserSsoSettings查询用户SSO身份提供商信息。|
|[CreateSAMLProvider](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/CreateSAMLProvider.md)|调用CreateSAMLProvider创建角色SSO身份提供商。|
|[GetSAMLProvider](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/GetSAMLProvider.md)|调用GetSAMLProvider查询角色SSO身份提供商信息。|
|[UpdateSAMLProvider](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/UpdateSAMLProvider.md)|调用UpdateSAMLProvider修改指定的角色SSO身份提供商信息。|
|[ListSAMLProviders](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/ListSAMLProviders.md)|调用ListSAMLProviders查询角色SSO身份提供商列表。|
|[DeleteSAMLProvider](/intl.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/DeleteSAMLProvider.md)|调用DeleteSAMLProvider删除指定的角色SSO身份提供商。|

## 安全设置API

|API|描述|
|---|--|
|[SetPasswordPolicy](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/SetPasswordPolicy.md)|调用SetPasswordPolicy设置RAM用户密码强度策略。|
|[GetPasswordPolicy](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GetPasswordPolicy.md)|调用GetPasswordPolicy查询RAM用户密码强度策略信息。|
|[SetSecurityPreference](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/SetSecurityPreference.md)|调用SetSecurityPreference设置RAM用户的全局安全首选项。|
|[GetSecurityPreference](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GetSecurityPreference.md)|调用GetSecurityPreference查询RAM用户的全局安全首选项。|
|[SetDefaultDomain](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/SetDefaultDomain.md)|调用SetDefaultDomain设置默认域名。|
|[GetDefaultDomain](/intl.zh-CN/API参考/API 参考（IMS）/安全设置/GetDefaultDomain.md)|调用GetDefaultDomain查询默认域名。|

