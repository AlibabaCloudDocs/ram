# List of operations by function

The following tables list the API operations that are available for use in Identity Management Service \(IMS\).

**Note:** Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.

## User management

|API|Description|
|---|-----------|
|[CreateUser](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateUser.md)|Creates a RAM user.|
|[GetUser](/intl.en-US/API Reference/API Reference (IMS)/User management/GetUser.md)|Queries the information of a RAM user.|
|[UpdateUser](/intl.en-US/API Reference/API Reference (IMS)/User management/UpdateUser.md)|Modifies the information of a RAM user.|
|[DeleteUser](/intl.en-US/API Reference/API Reference (IMS)/User management/DeleteUser.md)|Deletes a RAM user.|
|[ListUsers](/intl.en-US/API Reference/API Reference (IMS)/User management/ListUsers.md)|Queries the details of all RAM users.|
|[ListUserBasicInfos](/intl.en-US/API Reference/API Reference (IMS)/User management/ListUserBasicInfos.md)|Queries the basic information of all RAM users.|
|[CreateLoginProfile](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateLoginProfile.md)|Enables console logon for a RAM user.|
|[GetLoginProfile](/intl.en-US/API Reference/API Reference (IMS)/User management/GetLoginProfile.md)|Queries the logon information of a RAM user.|
|[UpdateLoginProfile](/intl.en-US/API Reference/API Reference (IMS)/User management/UpdateLoginProfile.md)|Modifies the logon information of a RAM user.|
|[DeleteLoginProfile](/intl.en-US/API Reference/API Reference (IMS)/User management/DeleteLoginProfile.md)|Disables console logon for a RAM user.|
|[ChangePassword](/intl.en-US/API Reference/API Reference (IMS)/User management/ChangePassword.md)|Changes the password that is used to log on to the console for a RAM user.|
|[CreateAccessKey](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateAccessKey.md)|Creates an AccessKey pair for an Alibaba Cloud account or a RAM user.|
|[UpdateAccessKey](/intl.en-US/API Reference/API Reference (IMS)/User management/UpdateAccessKey.md)|Modifies the status of an AccessKey pair for an Alibaba Cloud account or a RAM user.|
|[DeleteAccessKey](/intl.en-US/API Reference/API Reference (IMS)/User management/DeleteAccessKey.md)|Deletes an AccessKey pair from an Alibaba Cloud account or a RAM user.|
|[ListAccessKeys](/intl.en-US/API Reference/API Reference (IMS)/User management/ListAccessKeys.md)|Queries AccessKey pairs of an Alibaba Cloud account or a RAM user.|
|[GetAccessKeyLastUsed](/intl.en-US/API Reference/API Reference (IMS)/User management/GetAccessKeyLastUsed.md)|Queries the time when an AccessKey pair is used for the last time.|
|[CreateVirtualMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateVirtualMFADevice.md)|Creates a multi-factor authentication \(MFA\) device.|
|[ListVirtualMFADevices](/intl.en-US/API Reference/API Reference (IMS)/User management/ListVirtualMFADevices.md)|Queries MFA devices.|
|[DeleteVirtualMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/DeleteVirtualMFADevice.md)|Deletes an MFA device.|
|[DisableVirtualMFA](/intl.en-US/API Reference/API Reference (IMS)/User management/DisableVirtualMFA.md)|Unbinds and deletes an MFA device from a RAM user.|
|[BindMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/BindMFADevice.md)|Binds an MFA device to a RAM user.|
|[UnbindMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/UnbindMFADevice.md)|Unbinds an MFA device from a RAM user.|
|[GetAccountMFAInfo](/intl.en-US/API Reference/API Reference (IMS)/User management/GetAccountMFAInfo.md)|Queries the MFA status of an Alibaba Cloud account.|
|[GetUserMFAInfo](/intl.en-US/API Reference/API Reference (IMS)/User management/GetUserMFAInfo.md)|Queries the information of the MFA device that is bound to a RAM user.|
|[GenerateCredentialReport](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GenerateCredentialReport.md)|Generates a user credential report.|
|[GetCredentialReport](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GetCredentialReport.md)|Queries the content of a user credential report.|
|[GetAccountSecurityPracticeReport](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GetAccountSecurityPracticeReport.md)|Queries the security report of an Alibaba Cloud account.|
|[GetAccountSummary](/intl.en-US/API Reference/API Reference (IMS)/User management/GetAccountSummary.md)|Queries the overview information of an Alibaba Cloud account.|

## User group management

|API|Description|
|---|-----------|
|[CreateGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/CreateGroup.md)|Creates a RAM user group.|
|[GetGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/GetGroup.md)|Queries the information of a RAM user group.|
|[UpdateGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/UpdateGroup.md)|Modifies the information of a RAM user group.|
|[DeleteGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/DeleteGroup.md)|Deletes a RAM user group.|
|[ListGroups](/intl.en-US/API Reference/API Reference (IMS)/User group management/ListGroups.md)|Queries RAM user groups.|
|[AddUserToGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/AddUserToGroup.md)|Adds a RAM user to a RAM user group.|
|[ListUsersForGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/ListUsersForGroup.md)|Queries RAM users in a RAM user group.|
|[ListGroupsForUser](/intl.en-US/API Reference/API Reference (IMS)/User group management/ListGroupsForUser.md)|Queries the RAM user groups to which a RAM user belongs.|
|[RemoveUserFromGroup](/intl.en-US/API Reference/API Reference (IMS)/User group management/RemoveUserFromGroup.md)|Removes a RAM user from a RAM user group.|

## Single sign-on \(SSO\) management

|API|Description|
|---|-----------|
|[SetUserSsoSettings](/intl.en-US/API Reference/API Reference (IMS)/SSO management/SetUserSsoSettings.md)|Configures the information of identity providers \(IdPs\) for user-based SSO.|
|[GetUserSsoSettings](/intl.en-US/API Reference/API Reference (IMS)/SSO management/GetUserSsoSettings.md)|Queries the information of IdPs for user-based SSO.|
|[CreateSAMLProvider](/intl.en-US/API Reference/API Reference (IMS)/SSO management/CreateSAMLProvider.md)|Creates an IdP for role-based SSO.|
|[GetSAMLProvider](/intl.en-US/API Reference/API Reference (IMS)/SSO management/GetSAMLProvider.md)|Queries the information of an IdP for role-based SSO.|
|[UpdateSAMLProvider](/intl.en-US/API Reference/API Reference (IMS)/SSO management/UpdateSAMLProvider.md)|Modifies the information of an IdP for role-based SSO.|
|[ListSAMLProviders](/intl.en-US/API Reference/API Reference (IMS)/SSO management/ListSAMLProviders.md)|Queries IdPs for role-based SSO.|
|[DeleteSAMLProvider](/intl.en-US/API Reference/API Reference (IMS)/SSO management/DeleteSAMLProvider.md)|Deletes an IdP for role-based SSO.|

## Security settings

|API|Description|
|---|-----------|
|[SetPasswordPolicy](/intl.en-US/API Reference/API Reference (IMS)/Security settings/SetPasswordPolicy.md)|Configures the password policy for RAM users.|
|[GetPasswordPolicy](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GetPasswordPolicy.md)|Queries the password policy for RAM users.|
|[SetSecurityPreference](/intl.en-US/API Reference/API Reference (IMS)/Security settings/SetSecurityPreference.md)|Configures the security preferences for RAM users.|
|[GetSecurityPreference](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GetSecurityPreference.md)|Queries the security preferences of RAM users.|
|[SetDefaultDomain](/intl.en-US/API Reference/API Reference (IMS)/Security settings/SetDefaultDomain.md)|Configures the default domain name.|
|[GetDefaultDomain](/intl.en-US/API Reference/API Reference (IMS)/Security settings/GetDefaultDomain.md)|Queries the default domain name.|

