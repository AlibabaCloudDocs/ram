# RAM鉴权

RAM用户调用IMS API前，需要阿里云账号（主账号）创建权限策略并对RAM用户进行授权。在权限策略中，使用资源描述符（Alibaba Cloud Resource Name，ARN）指定授权资源。

## 用户管理鉴权列表

下表列举了用户管理中可授权的操作（Action）和资源（Resource）。

|Action|Resource|
|------|--------|
|ims:CreateUser|acs:ims::$\{AccountId\}:user/\*|
|ims:GetUser|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:UpdateUser|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:DeleteUser|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:ListUsers|acs:ims::$\{AccountId\}:user/\*|
|ims:ListUserBasicInfos|acs:ims::$\{AccountId\}:user/\*|
|ims:CreateLoginProfile|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:GetLoginProfile|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:UpdateLoginProfile|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:DeleteLoginProfile|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:CreateAccessKey|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:UpdateAccessKey|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:DeleteAccessKey|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:ListAccessKeys|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:GetAccessKeyLastUsed|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:CreateVirtualMFADevice|acs:ims::$\{AccountId\}:mfa/\*|
|ims:ListVirtualMFADevices|acs:ims::$\{AccountId\}:mfa/\*|
|ims:DeleteVirtualMFADevice|$\{SerialNumber\}|
|ims:DisableVirtualMFA|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:BindMFADevice|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:UnbindMFADevice|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:GetAccountMFAInfo|acs:ims::$\{AccountId\}:\*|
|ims:GetUserMFAInfo|acs:ims::$\{AccountId\}:user/$\{UserName\}|
|ims:GetAccountSummary|acs:ims::$\{AccountId\}:\*|

## 用户组管理鉴权列表

下表列举了用户组管理中可授权的操作（Action）和资源（Resource）。

|Action|Resource|
|------|--------|
|ims:CreateGroup|acs:ims::$\{AccountId\}:group/\*|
|ims:GetGroup|acs:ims::$\{AccountId\}:group/$\{GroupName\}|
|ims:UpdateGroup|acs:ims::$\{AccountId\}:group/$\{GroupName\}|
|ims:DeleteGroup|acs:ims::$\{AccountId\}:group/$\{GroupName\}|
|ims:ListGroups|acs:ims::$\{AccountId\}:group/\*|
|ims:AddUserToGroup|-   acs:ims::$\{AccountId\}:user/$\{UserName\}
-   acs:ims::$\{AccountId\}:group/$\{GroupName\} |
|ims:RemoveUserFromGroup|-   acs:ims::$\{AccountId\}:user/$\{UserName\}
-   acs:ims::$\{AccountId\}:group/$\{GroupName\} |
|ims:ListUsersForGroup|acs:ims::$\{AccountId\}:group/$\{GroupName\}|
|ims:ListGroupsForUser|acs:ims::$\{AccountId\}:user/$\{UserName\}|

## 单点登录（SSO）管理鉴权列表

下表列举了单点登录（SSO）管理中可授权的操作（Action）和资源（Resource）。

|Action|Resource|
|------|--------|
|ims:SetUserSsoSettings|acs:ims::$\{AccountId\}:\*|
|ims:GetUserSsoSettings|acs:ims::$\{AccountId\}:\*|
|ims:CreateSAMLProvider|acs:ims::$\{AccountId\}:saml-provider/\*|
|ims:GetSAMLProvider|acs:ims::$\{AccountId\}:saml-provider/$\{SamlProviderName\}|
|ims:UpdateSAMLProvider|acs:ims::$\{AccountId\}:saml-provider/$\{SamlProviderName\}|
|ims:ListSAMLProviders|acs:ims::$\{AccountId\}:saml-provider/\*|
|ims:DeleteSAMLProvider|acs:ims::$\{AccountId\}:saml-provider/$\{SamlProviderName\}|

## 安全设置鉴权列表

下表列举了安全设置中可授权的操作（Action）和资源（Resource）。

|Action|Resource|
|------|--------|
|ims:SetPasswordPolicy|acs:ims::$\{AccountId\}:\*|
|ims:GetPasswordPolicy|acs:ims::$\{AccountId\}:\*|
|ims:SetSecurityPreference|acs:ims::$\{AccountId\}:\*|
|ims:GetSecurityPreference|acs:ims::$\{AccountId\}:\*|
|ims:SetDefaultDomain|acs:ims::$\{AccountId\}:\*|
|ims:GetDefaultDomain|acs:ims::$\{AccountId\}:\*|
|ims:GenerateCredentialReport|acs:ims::$\{AccountId\}:\*|
|ims:GetCredentialReport|acs:ims::$\{AccountId\}:\*|
|ims:GetAccountSecurityPracticeReport|acs:ims::$\{AccountId\}:\*|

