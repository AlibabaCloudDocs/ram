# RAM role overview

A RAM role is a virtual RAM identity that you can create within your Alibaba Cloud account. A RAM role does not have a specific logon password or AccessKey pair. A RAM role can be used only after the RAM role is assumed by a trusted entity.

## Terms

|Term|Description|
|----|-----------|
|RAM role|A RAM role is a virtual identity that you can create within your Alibaba Cloud account. RAM roles, entity users \(Alibaba Cloud accounts, RAM users, or Alibaba Cloud services\), and textbook roles have the following differences:-   Entity users have logon passwords or AccessKey pairs.
-   Textbook roles \(or traditionally defined roles\) indicate a set of permissions, which are similar to policies in RAM. If a user assumes a textbook role, the user can obtain a set of permissions and access the authorized resources.
-   RAM roles are identities to which permission policies are attached. However, RAM roles do not have logon passwords or AccessKey pairs. If an entity user assumes a RAM role, the entity user can obtain and use the Security Token Service \(STS\) token of the role to access the authorized resources. |
|Role ARN|The Alibaba Cloud Resource Name \(ARN\) of a RAM role is the globally unique resource identifier of the RAM role. Role ARNs follow the ARN naming conventions that are provided by Alibaba Cloud. For example, the ARN of the devops RAM role of an Alibaba Cloud account is `acs:ram::123456789012****:role/samplerole`. After you create a RAM role, you can click the role name and find its ARN in the **Basic Information** section.|
|trusted entity|A trusted entity indicates an entity user who can assume a role. When you create a role, you must specify a trusted entity. A RAM role can be assumed only by a trusted entity. A trusted entity can be an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\).|
|policy|Each RAM role can be attached one or more polices. RAM roles without policies can exist, but cannot access Alibaba Cloud resources.|
|role assuming|Role assuming is the method for entity users to obtain STS tokens of RAM roles. An entity user can call the AssumeRole STS API operation to obtain the STS token of a RAM role. Then, the entity user can use the STS token to call API operations of Alibaba Cloud services.|
|Identity switching|Identity switching is the method by which entity users can switch from the logon identity to the role identity in the RAM console. After an entity user logs on to the RAM console, the entity user can switch to a RAM role that the entity user can assume. Then, the entity user can use the RAM role to manage Alibaba Cloud resources. After the management operations are complete, the RAM user can switch back to the logon identity.|
|role token|A role token is a temporary AccessKey pair for a RAM role. A RAM role does not have a specific logon password or AccessKey pair. If an entity user wants to use a RAM role, the entity user must assume the RAM role to obtain a role token. Then, the entity user can use the role token to call API operations of Alibaba Cloud services.|

## Access Alibaba Cloud resources by using a RAM role

1.  The Alibaba Cloud account specifies a trusted entity that can assume the RAM role.
2.  The trusted entity logs on to the console or calls an API operation to assume the RAM role, and obtains a role token.

    ![Terms](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1980549951/p14225.png)

    -   The trusted entity can switch the identity in the console to assume the RAM role. For more information, see [Assume a RAM role](/intl.en-US/RAM Role Management/Assume a RAM role.md).
    -   The trusted entity can also call the AssumeRole API operation to assume the RAM role.
    **Note:** An entity user can obtain a role token by assuming a RAM role and then use the role token to access Alibaba Cloud resources.

3.  The Alibaba Cloud account attaches a policy to the RAM role. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

    **Note:** Each RAM role can be attached one or more polices. RAM roles without policies can exist, but cannot access Alibaba Cloud resources.

4.  The trusted entity assumes the RAM role and uses the role token to access Alibaba Cloud resources.

## RAM role types

RAM roles are classified into three types based on trusted entities, as described in the following table.

|Role type|Scenario|Documentation|
|---------|--------|-------------|
|Alibaba Cloud account|RAM users within an Alibaba Cloud account can assume this type of RAM role. RAM users who assume this type of RAM role can belong to their parent Alibaba Cloud accounts or other Alibaba Cloud accounts. This type of RAM role is used for cross-account access and temporary authorization.|-   [Use an STS token for authorizing a mobile app to access Alibaba Cloud resources](/intl.en-US/Tutorials/Use an STS token for authorizing a mobile app to access Alibaba Cloud resources.md)
-   [Use a RAM role to grant permissions across Alibaba Cloud accounts](/intl.en-US/Tutorials/Use a RAM role to grant permissions across Alibaba Cloud accounts.md) |
|Alibaba Cloud service|Alibaba Cloud services can assume this type of RAM role. This type of RAM role is used to authorize the access across Alibaba Cloud services.|-   [Use RAM for authorizing applications to access Alibaba Cloud resources](/intl.en-US/Tutorials/Use RAM for authorizing applications to access Alibaba Cloud resources.md)
-   [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md) |
|Identity provider \(IdP\)|Users of a trusted IdP can assume this type of RAM role. This type of RAM role is used to implement single sign-on \(SSO\) between Alibaba Cloud and a trusted IdP.|-   [Implement role-based SSO by using Active Directory Federation Services](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO by using Active Directory Federation Services.md)
-   [Implement role-based SSO from Okta](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO from Okta.md)
-   [Implement role-based SSO by using Azure Active Directory](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO by using Azure Active Directory.md) |

