# API overview

The following table describes common scenarios and the API operations that can be called in those scenarios.

|Scenario|Description|API selection|Difference|
|--------|-----------|-------------|----------|
|User management|Manage Resource Access Management \(RAM\) users, AccessKey pairs, logon passwords, and multi-factor authentication \(MFA\) devices.|-   [IMS API](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md)
-   [RAM API](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md)

|-   Some of the RAM API operations have the same features as Identity Management Service \(IMS\) API operations. You can call these RAM API operations or IMS API operations to achieve the same results.
-   IMS API operations support more new features. For example, you can call IMS API operations to query the time when an AccessKey pair was last used, modify the default domain name, and obtain user credential reports.
-   New features related to user management, user group management, and security settings will be supported by IMS API operations. Therefore, we recommend that you use IMS API operations. |
|User group management|Manage RAM user groups, and add or remove RAM users in RAM user groups.|
|Security settings|Manage password policies, global security preferences, default domain names, user credential reports, and security reports of Alibaba Cloud accounts.|
|Policy management|Manage policies and grant permissions to or revoke permissions from a RAM user, RAM role, or RAM user group.|-   [RAM API](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md)
-   [Resource Management API]()

|-   Some of the RAM API operations have the same features as Resource Management API operations. You can call these RAM API operations or Resource Management API operations to achieve the same results.
-   You can call the Resource Management API to grant permissions to a resource group. You cannot call the RAM API to grant permissions to a resource group.
-   Resource Management API operations support more new features, such as service-linked roles.
-   Resource Management API operations are easy to use. For example, you can call the AttachPolicy operation to grant permissions to a RAM user, a RAM role, or a RAM user group.
-   New features related to policy management and user management will be supported by Resource Management API operations. Therefore, we recommend that you use Resource Management API operations. |
|Role management|Manage RAM roles.|
|Role usage|Assume a RAM role by using a Security Token Service \(STS\) token.|[STS API](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md)|None.|
|Single sign-on \(SSO\) management|Manage identity providers \(IdPs\) for user-based SSO and role-based SSO.|[IMS API](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md)|None.|
|Role-based SSO usage|Use an STS token for role-based SSO.|[STS API](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md)|None.|
|Open authorization \(OAuth \) management|Manage applications and application secrets.|[IMS API](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md)|None.|

