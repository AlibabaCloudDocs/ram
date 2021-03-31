# Terms

This topic describes the terms that are used in Resource Access Management \(RAM\).

## Terms for identity management

|Term|Description|
|----|-----------|
|Alibaba Cloud account|Before you use Alibaba Cloud services, you must create an Alibaba Cloud account. The Alibaba Cloud account is the owner of Alibaba Cloud resources. The Alibaba Cloud account is charged for all of the resources that it owns. The Alibaba Cloud account has full control over the resources.

By default, only the Alibaba Cloud account can access Alibaba Cloud resources. Other users can access resources only after being explicitly authorized by the Alibaba Cloud account. The Alibaba Cloud account is the administrator or root user of an operating system. |
|identity|RAM provides three types of identities: RAM user, RAM user group, and RAM role. RAM users and RAM user groups are physical identities. RAM roles are virtual identities.|
|default domain name|A unique identifier of an Alibaba Cloud account. Alibaba Cloud assigns a **default domain name** to each Alibaba Cloud account. The format of the default domain name is `<AccountAlias>.onaliyun.com`. This unique identifier can be used for RAM user logonand single sign-on \(SSO\).

For more information, see [Manage the default domain name](/intl.en-US/Security Settings/Advanced settings/Manage the default domain name.md). |
|account alias or enterprise alias|A unique identifier of an Alibaba Cloud account. When a RAM user logs on to the Alibaba Cloud Management Console, the suffix of the logon name can be the account alias, default domain name, or domain alias.

Each Alibaba Cloud account can have an account alias. The account alias is used for RAM user logon and can be displayed after successful logon.

For example, an enterprise can set the account alias of its Alibaba Cloud account to company1. The RAM user named alice that belongs to this Alibaba Cloud account can log on to the Alibaba Cloud Management Console by using alice@company1. After successful logon, the display name of the RAM user is alice@company1. |
|domain alias|A custom domain name that can be used to replace the default domain name. The custom domain name must be publicly resolvable.**** A domain alias is the alias of the default domain name.

**Note:** A domain alias can be used only after domain ownership verification. After verification, you can use the domain alias to replace the default domain name in all scenarios where the default domain name is required.

For more information, see [Create and verify a domain alias](/intl.en-US/Security Settings/Advanced settings/Create and verify a domain alias.md). |
|RAM user|A physical identity that has a fixed ID and credential information. A RAM user represents a person or an application.

-   An Alibaba Cloud account can create multiple RAM users. RAM users can be used to represent employees, systems, and applications within an enterprise.
-   RAM users do not own resources. Fees that are incurred by RAM users are billed to their parent Alibaba Cloud accounts. RAM users do not receive individual bills and cannot make payments.
-   RAM users are visible only to their parent Alibaba Cloud account.
-   Before RAM users can log on to the Alibaba Cloud Management Console or call API operations, they must be authorized by Alibaba Cloud accounts. After authorization, RAM users can use resources that are owned by the Alibaba Cloud accounts.

For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md). |
|password|An identity credential that is used to log on to the Alibaba Cloud Management Console.

**Note:** You cannot query the logon password. We recommend that you change your password on a regular basis and keep your password confidential.

For more information, see [Change the password for an Alibaba Cloud account](/intl.en-US/Security Settings/Passwords/Change the password for an Alibaba Cloud account.md) and [Change the password of a RAM user](/intl.en-US/Security Settings/Passwords/Change the password of a RAM user.md). |
|AccessKey pair|An identity credential that is used to verify access identities. Each AccessKey pair consists of an AccessKey ID and an AccessKey secret. You can use your AccessKey pair or Alibaba Cloud SDK to sign API requests that you send to Alibaba Cloud. The AccessKey ID and AccessKey secret are used for symmetric encryption and identity verification. After the identity is verified, you can manage Alibaba Cloud resources by calling API operations.

An AccessKey ID is used in combination with an AccessKey secret. The AccessKey ID is used to identify a user, and the AccessKey secret is used to authenticate the key of the user.

**Note:** An AccessKey secret is displayed only when you create the AccessKey pair, and cannot be queried. We recommend that you save the AccessKey secret for subsequent use.

For more information, see [Create an AccessKey pair for a RAM user](/intl.en-US/Security Settings/AccessKey pairs/Create an AccessKey pair for a RAM user.md). |
|multi-factor authentication \(MFA\)|A simple best practice that adds an extra layer of protection in addition to your username and password. MFA enhances security for your account. If MFA is enabled for a user, the user must perform the following operations when the user logs on to the Alibaba Cloud Management Console:

1.  Enter the username and password of the RAM user.
2.  Enter the verification code that is generated by the virtual MFA device or pass the Universal 2nd Factor \(U2F\) authentication.

For more information, see [Enable an MFA device for an Alibaba Cloud account](/intl.en-US/Security Settings/Multi-factor authentication/Enable an MFA device for an Alibaba Cloud account.md) and [Enable an MFA device for a RAM user](/intl.en-US/Security Settings/Multi-factor authentication/Enable an MFA device for a RAM user.md). |
|RAM user group|A physical identity that contains a group of RAM users. You can create RAM user groups to classify and authorize RAM users. This simplifies the management of personnel and permissions.

-   If the responsibilities of a RAM user change, you only need to move the RAM user to a RAM user group with the required permissions. This does not affect other RAM users.

For more information, see [Create a RAM user group](/intl.en-US/RAM User Group Management/Create a RAM user group.md).

-   If the responsibilities of a RAM user group change, you only need to modify the policy that is attached to the group. The changes to the policy apply to all RAM users in the RAM user group.

For more information, see [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md). |
|RAM role|A RAM role is a virtual identity that you can create within your Alibaba Cloud account. RAM roles, entity users \(Alibaba Cloud accounts, RAM users, or Alibaba Cloud services\), and textbook roles have the following differences:

-   Entity users have logon passwords or AccessKey pairs.
-   Textbook roles \(or traditionally defined roles\) indicate a set of permissions, which are similar to policies in RAM. If a user assumes a textbook role, the user can obtain a set of permissions and access the required resources.
-   RAM roles are identities to which permission policies are attached. However, RAM roles do not have logon passwords or AccessKey pairs. If an entity user assumes a RAM role, the entity user can obtain and use the Security Token Service \(STS\) token of the role to access the required resources.

RAM roles are divided into the following types based on trusted entities:

-   **Alibaba Cloud account**: RAM users of a trusted Alibaba Cloud account can assume this type of RAM role. RAM users who assume this type of RAM role can belong to their parent Alibaba Cloud accounts or other Alibaba Cloud accounts. This type of RAM role is used for cross-account access and temporary authorization.
-   **Alibaba Cloud service**: Alibaba Cloud services can assume this type of RAM role. This type of RAM role is used to authorize Alibaba Cloud services to manage your resources.
-   **IdP**: Users of a trusted identity provider \(IdP\) can assume this type of RAM role. The RAM roles of this type are used to implement SSO between Alibaba Cloud and a trusted IdP.

For more information, see [Create a RAM role for a trusted Alibaba Cloud account](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud account.md), [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md), and [Create a RAM role for a trusted Alibaba Cloud service](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md). |
|service provider \(SP\)|An application that uses the identity management feature of an IdP to provide users with specific services. An SP uses the user information that is provided by an IdP. In some identity systems \(such as OpenID Connect\) that do not comply with the SAML protocol, SP is known as the relying party of an IdP.|
|identity provider \(IdP\)|A RAM entity that provides identity management services. IdPs are classified into the following types:

-   IdPs that use the on-premises architecture, such as Microsoft Active Directory Federation Service \(AD FS\) and Shibboleth
-   IdPs that use the cloud-based architecture, such as Azure AD, Google G Suite, Okta, and OneLogin |
|Security Assertion Markup Language 2.0 \(SAML 2.0\)|A protocol that is designed for enterprise-level user identity authentication. SAML 2.0 is used for communication between an SP and an IdP. SAML 2.0 is a standard that enterprises use to implement enterprise-level SSO.|
|single sign-on \(SSO\)|Alibaba Cloud supports SAML 2.0-based SSO. This feature is also known as identity federation.

You can implement SSO between Alibaba Cloud and your IdP, such as Microsoft Active Directory Federation Service \(AD FS\), based on SAML 2.0. Alibaba Cloud provides the following two SAML 2.0-based SSO methods:

-   User-based SSO: The RAM user identity that you can use to log on to the Alibaba Cloud Management Console is determined based on an SAML assertion. After you log on to the Alibaba Cloud Management Console, you can access Alibaba Cloud resources as a RAM user. For more information, see [Overview of user-based SSO](/intl.en-US/SSO Management/User-based SSO/Overview of user-based SSO.md).
-   Role-based SSO: The RAM role that you can use to log on to the Alibaba Cloud Management Console is determined based on an SAML assertion. After you log on to the Alibaba Cloud Management Console, you can use the RAM role that is specified in the SAML assertion to access Alibaba Cloud resources. For more information, see [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md). |
|metadata file|The metadata file that is provided by your IdP. The metadata file is in the XML format in most cases. The metadata file contains the logon URLs, the public key that is used to verify SAML assertions, and the assertion format.|
|SAML assertion|A core element that is defined in the SAML protocol. This element describes the authentication request and response. For example, the SAML assertion for an authentication response can contain user attributes.|
|trust|A mutual trust relationship between an SP and an IdP. In most cases, the trust relationship is established by using public and private keys. An SP can obtain the SAML metadata of a trusted IdP. The metadata includes a public key. The SP uses the public key to verify the integrity of the SAML assertion that is issued by the IdP.|

## Terms for access control

|Term|Description|
|----|-----------|
|permission|Indicates whether a user is allowed to perform specific operations on a specific Alibaba Cloud resource. Permissions include Allow and Deny.

Operations include the following two types:

-   Resource management operations: the lifecycle management and O&M of Alibaba Cloud resources. These operations are performed by the Alibaba Cloud account that purchases the resources or by O&M staff in an organization. For example, an authorized user can create, stop, or restart Elastic Compute Service \(ECS\) instances, or create, modify, or delete Object Storage Service \(OSS\) buckets.
-   Resource using operations: using the core features of Alibaba Cloud resources. These operations are performed by R&D staff or applications in an organization. For example, an authorized user can perform operations in the operating system of an ECS instance, or upload or download data in an OSS bucket.

**Note:**

    -   For elastic computing and database products, the permissions on resource management operations can be managed by using RAM. However, the permissions on resource using operations are managed in product instances. For example, the permissions on the operating systems are managed in ECS instances and the permissions on MySQL databases are managed in ApsaraDB RDS instances.
    -   For storage products, such as OSS and Tablestore, both resource management operations and resource using operations can be managed by using RAM. |
|policy|A set of permissions that are described based on the policy structure and syntax. You can use policies to describe the authorized resource sets, authorized operation sets, and authorization conditions. For more information, see [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

In RAM, a policy is a resource entity that can be created, updated, deleted, and viewed. RAM supports the following two types of policy:

-   **System policy**: System policies are created and updated by Alibaba Cloud and cannot be modified by users.
-   **Custom policy**: Custom policies are created, modified, and deleted by users to meet their business requirements.

You can attach one or more policies to RAM users, RAM user groups, and RAM roles. For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md), [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md), and [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md). |
|principal|The subject to which a specific permission is granted. The authorized principal can be a RAM user, RAM user group, or RAM role.|
|effect|The authorization effect. It is a basic element of a policy. Valid values are Allow and Deny.|
|action|The operations to be performed on a specific Alibaba Cloud resource. The action is a basic element of a policy. Valid values are the names of API operations from Alibaba Cloud services.|
|condition|The condition for the authorization to take effect. The condition is a basic element of a policy.|
|Resource|A manageable object that is provided by an Alibaba Cloud service. For example, resources can be OSS buckets and ECS instances.|

