# API概览

IMS（Identity Management Service）提供以下相关API。

**说明：** [OpenAPI开发者门户](https://next.api.aliyun.com/product/Ims)提供在线调试API的功能，能显著降低API的使用难度，推荐您使用。

## 用户管理API

|API|描述|
|---|--|
|[CreateUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateUser.md)|调用CreateUser创建RAM用户。|
|[GetUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetUser.md)|调用GetUser查询RAM用户的详细信息。|
|[UpdateUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateUser.md)|调用UpdateUser修改RAM用户信息。|
|[DeleteUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteUser.md)|调用DeleteUser删除RAM用户。|
|[ListUsers](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/ListUsers.md)|调用ListUsers查询所有RAM用户的详细信息。|
|[ListUserBasicInfos](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/ListUserBasicInfos.md)|调用ListUserBasicInfos查询所有RAM用户的基本信息。|
|[CreateLoginProfile](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateLoginProfile.md)|调用CreateLoginProfile开启指定RAM用户的控制台登录。|
|[GetLoginProfile](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetLoginProfile.md)|调用GetLoginProfile查询指定RAM用户的控制台登录信息。|
|[UpdateLoginProfile](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateLoginProfile.md)|调用UpdateLoginProfile修改指定RAM用户的控制台登录信息。|
|[DeleteLoginProfile](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteLoginProfile.md)|调用DeleteLoginProfile关闭指定RAM用户的控制台登录。|
|[ChangePassword](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/ChangePassword.md)|RAM用户调用ChangePassword修改自己的控制台登录密码。|
|[CreateAccessKey](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateAccessKey.md)|调用CreateAccessKey创建阿里云账号（主账号）或RAM用户的访问密钥。|
|[UpdateAccessKey](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/UpdateAccessKey.md)|调用UpdateAccessKey修改阿里云账号（主账号）或RAM用户的访问密钥状态。|
|[DeleteAccessKey](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteAccessKey.md)|调用DeleteAccessKey删除阿里云账号（主账号）或RAM用户的访问密钥。|
|[ListAccessKeys](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/ListAccessKeys.md)|调用ListAccessKeys查询阿里云账号（主账号）或RAM用户的访问密钥列表。|
|[GetAccessKeyLastUsed](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccessKeyLastUsed.md)|调用GetAccessKeyLastUsed查询指定访问密钥的最后使用时间。|
|[CreateVirtualMFADevice](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateVirtualMFADevice.md)|调用CreateVirtualMFADevice创建多因素认证设备。|
|[ListVirtualMFADevices](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/ListVirtualMFADevices.md)|调用ListVirtualMFADevices查询多因素认证设备列表。|
|[DeleteVirtualMFADevice](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteVirtualMFADevice.md)|调用DeleteVirtualMFADevice删除多因素认证设备。|
|[DisableVirtualMFA](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/DisableVirtualMFA.md)|调用DisableVirtualMFA解绑并删除指定RAM用户的多因素认证设备。|
|[BindMFADevice](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/BindMFADevice.md)|调用BindMFADevice为RAM用户绑定多因素认证设备。|
|[UnbindMFADevice](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/UnbindMFADevice.md)|调用UnbindMFADevice为RAM用户解绑多因素认证设备。|
|[GetAccountMFAInfo](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccountMFAInfo.md)|调用GetAccountMFAInfo查询阿里云账号（主账号）的多因素认证设备信息。|
|[GetUserMFAInfo](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetUserMFAInfo.md)|调用GetUserMFAInfo查询RAM用户绑定的多因素认证设备信息。|
|[GenerateCredentialReport](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GenerateCredentialReport.md)|调用GenerateCredentialReport生成用户凭证报告。|
|[GetCredentialReport](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GetCredentialReport.md)|调用GetCredentialReport查询用户凭证报告内容。|
|[GetAccountSecurityPracticeReport](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GetAccountSecurityPracticeReport.md)|调用GetAccountSecurityPracticeReport查询阿里云账号的安全报告。|
|[GetAccountSummary](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/GetAccountSummary.md)|调用GetAccountSummary查询阿里云账号（主账号）的概览信息。|

## 用户组管理API

|API|描述|
|---|--|
|[CreateGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/CreateGroup.md)|调用CreateGroup创建用户组。|
|[GetGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/GetGroup.md)|调用GetGroup查询指定用户组信息。|
|[UpdateGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/UpdateGroup.md)|调用UpdateGroup修改指定用户组的信息。|
|[DeleteGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/DeleteGroup.md)|调用DeleteGroup删除指定的用户组。|
|[ListGroups](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/ListGroups.md)|调用ListGroups查询用户组列表。|
|[AddUserToGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/AddUserToGroup.md)|调用AddUserToGroup将RAM用户添加到指定的用户组。|
|[ListUsersForGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/ListUsersForGroup.md)|调用ListUsersForGroup查询指定用户组内的RAM用户列表。|
|[ListGroupsForUser](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/ListGroupsForUser.md)|调用ListGroupsForUser查询指定RAM用户加入的用户组列表。|
|[RemoveUserFromGroup](/cn.zh-CN/API参考/API 参考（IMS）/用户组管理/RemoveUserFromGroup.md)|调用RemoveUserFromGroup将RAM用户从用户组中移除。|

## 单点登录（SSO）管理API

|API|描述|
|---|--|
|[SetUserSsoSettings](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/SetUserSsoSettings.md)|调用SetUserSsoSettings设置用户SSO身份提供商信息。|
|[GetUserSsoSettings](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/GetUserSsoSettings.md)|调用GetUserSsoSettings查询用户SSO身份提供商信息。|
|[CreateSAMLProvider](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/CreateSAMLProvider.md)|调用CreateSAMLProvider创建角色SSO身份提供商。|
|[GetSAMLProvider](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/GetSAMLProvider.md)|调用GetSAMLProvider查询角色SSO身份提供商信息。|
|[UpdateSAMLProvider](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/UpdateSAMLProvider.md)|调用UpdateSAMLProvider修改指定的角色SSO身份提供商信息。|
|[ListSAMLProviders](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/ListSAMLProviders.md)|调用ListSAMLProviders查询角色SSO身份提供商列表。|
|[DeleteSAMLProvider](/cn.zh-CN/API参考/API 参考（IMS）/单点登录（SSO）管理/DeleteSAMLProvider.md)|调用DeleteSAMLProvider删除指定的角色SSO身份提供商。|

## 开放授权（OAuth）管理API

|API|描述|
|---|--|
|[CreateApplication](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/CreateApplication.md)|调用CreateApplication创建应用。|
|[GetApplication](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/GetApplication.md)|调用GetApplication查询应用的配置信息。|
|[UpdateApplication](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/UpdateApplication.md)|调用UpdateApplication修改应用的配置信息。|
|[DeleteApplication](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/DeleteApplication.md)|调用DeleteApplication删除一个应用。|
|[ListApplications](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/ListApplications.md)|调用ListApplications查询应用列表。|
|[ListPredefinedScopes](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/ListPredefinedScopes.md)|调用ListPredefinedScopes查询系统预定义的应用范围列表。|
|[CreateAppSecret](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/CreateAppSecret.md)|调用CreateAppSecret为指定的应用创建应用密钥。|
|[GetAppSecret](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/GetAppSecret.md)|调用GetAppSecret查询指定应用密钥信息。|
|[DeleteAppSecret](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/DeleteAppSecret.md)|调用DeleteAppSecret删除指定的应用密钥。|
|[ListAppSecretIds](/cn.zh-CN/API参考/API 参考（IMS）/开放授权（OAuth）管理/ListAppSecretIds.md)|调用ListAppSecretIds查询指定应用的访问密钥ID列表。|

## 安全设置API

|API|描述|
|---|--|
|[SetPasswordPolicy](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/SetPasswordPolicy.md)|调用SetPasswordPolicy设置RAM用户密码强度策略。|
|[GetPasswordPolicy](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GetPasswordPolicy.md)|调用GetPasswordPolicy查询RAM用户密码强度策略信息。|
|[SetSecurityPreference](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/SetSecurityPreference.md)|调用SetSecurityPreference设置RAM用户的全局安全首选项。|
|[GetSecurityPreference](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GetSecurityPreference.md)|调用GetSecurityPreference查询RAM用户的全局安全首选项。|
|[SetDefaultDomain](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/SetDefaultDomain.md)|调用SetDefaultDomain设置默认域名。|
|[GetDefaultDomain](/cn.zh-CN/API参考/API 参考（IMS）/安全设置/GetDefaultDomain.md)|调用GetDefaultDomain查询默认域名。|

