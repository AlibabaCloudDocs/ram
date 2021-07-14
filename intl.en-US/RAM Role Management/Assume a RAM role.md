# Assume a RAM role

This topic describes how a Resource Access Management \(RAM\) user uses the Alibaba Cloud Management Console and API to assume a RAM role whose trusted entity is an Alibaba Cloud account.

Before you can assume a RAM role, make sure that you have completed the following operations:

1.  [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).
2.  Create an AccessKey pair or configure a logon password for the RAM user.
    -   For more information about how to configure a logon password, see [Change the password of a RAM user](/intl.en-US/Security Settings/Passwords/Change the password of a RAM user.md).
    -   For more information about how to create an AccessKey pair, see [Create an AccessKey pair for a RAM user](/intl.en-US/Security Settings/AccessKey pairs/Create an AccessKey pair for a RAM user.md).
3.  [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).
    -   You can attach the `AliyunSTSAssumeRoleAccess` system policy to the RAM user. This way, the RAM user can assume all RAM roles.
    -   To specify the RAM role that the RAM user can assume, you can attach a custom policy to the RAM user. For more information, see [Can I specify the RAM role that a RAM user can assume?](/intl.en-US/FAQ/FAQ about RAM roles and STS tokens.md).

## Use the Alibaba Cloud Management Console

To assume a RAM role, a RAM user must log on to the RAM console and switch the logon identity to the RAM role.The RAM user can either log on to the RAM console by using a password or using role-based single sign-on \(SSO\).

1.  Log on to the [RAM console](https://signin.alibabacloud.com/login.htm) as a RAM user.

2.  Move the pointer over the profile picture in the upper-right corner. Find and copy the value of the **Enterprise Alias** field and click **Switch Identity**.

3.  On the **Switch Role** page, enter the alias that you copied earlier and specify the Role Name parameter.

    **Note:** On the **Switch Role** page, you can also enter the default domain name or your Alibaba Cloud account in the Enterprise Alias / Domain / Account UID field. For more information, see [View and modify the default domain name](/intl.en-US/Security Settings/Advanced settings/Manage the default domain name.md).

4.  Click **Commit**.

    After the switch is complete, your logon identity changes to the RAM role, and you have the permissions that are granted to the RAM role.

    When you move the pointer over the profile picture in the upper-right corner of the Alibaba Cloud Management Console, you can view the logon identity and current identity. The following table describes the logon identity and current identity. The My Identity field shows the current identity.

    |Logon type|Logon identity|Current identity|
    |----------|--------------|----------------|
    |Password-based logon|The format is <Username of the logon RAM user\>.

|The format is <RoleName\>/<RoleSessionName\>.

    -   RoleName: the name of the role that is assumed by the RAM user
    -   RoleSessionName: the username of the RAM user |
    |Role-based SSO|After you log on to the RAM console as a RAM role, the current identity is displayed. The logon identity is not displayed.

If you switch the identity to another RAM role, the logon identity is displayed in the format of <RoleName\>/<RoleSessionName\>.

    -   RoleName: the name of the role that is used for SSO
    -   RoleSessionName: the RoleSessionName attribute in the role-based SSO authentication response
For example, if the tom@example.local user of a trusted IdP logs on to the Alibaba Cloud Management Console as the RAM role test-saml-role1 and switches the identity to the RAM role alice-testrole, the logon identity is test-saml-role1/tom@example.local.

|The format is <RoleName\>/<RoleSessionName\>.

    -   RoleName: the name of the role that is assumed
    -   RoleSessionName: the RoleSessionName attribute in the role-based SSO authentication response
For example, if the tom@example.local user of a trusted IdP logs on to the Alibaba Cloud Management Console as the RAM role test-saml-role1 and switches the identity to the RAM role alice-testrole, the current identity is alice-testrole/tom@example.local. The value of RoleSessionName remains unchanged. |

    The smaller value of the **Maximum Session Duration** and **Logon Session Valid For** parameters is used as the maximum duration of the logon session. For more information, see [Specify the maximum session duration for a RAM role](/intl.en-US/RAM Role Management/Specify the maximum session duration for a RAM role.md) and [Set security policies for RAM users](/intl.en-US/Security Settings/Basic security settings/Set security policies for RAM users.md).


## Use the API

An authorized RAM user can use an AccessKey pair to call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation. This way, the RAM user obtains an STS token and can use the STS token to access Alibaba Cloud resources.

**Note:** If STS tokens that you obtain after you assume RAM roles are leaked, you can disable all the STS tokens. For more information, see [What do I do if STS tokens are disclosed?](/intl.en-US/FAQ/FAQ about RAM roles and STS tokens.md).

## References

For information about how to log on to the Alibaba Cloud Management Console by using role-based SSO, see [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md).

