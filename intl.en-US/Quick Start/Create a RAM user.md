# Create a RAM user

This topic describes how to create a RAM user. A RAM user is an entity that you create in RAM to represent a person or application. A RAM user can access Alibaba Cloud resources after the RAM user is granted the required permissions.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  In the left-side navigation pane, click **Users** under **Identities**.

3.  On the Users page, click **Create User**.

    **Note:** You can click **Add User** to create multiple RAM users at a time.

4.  Set the **Logon Name** and **Display Name** parameters.

5.  In the **Access Mode** section, select **Console Password Logon** or **Programmatic Access**.

    -   **Console Password Logon**: If you select this access mode, you must complete the logon security settings. These settings specify whether to use a system-generated or custom logon password, whether the password must be reset on the next logon, and whether to enable multi-factor authentication \(MFA\).

        **Note:** If you select Custom Logon Password in the Console Password section, you must specify a password. The password must meet the strength requirements that you have specified on the **Identities** \> **Settings** page. For more information, see [Set a password policy for RAM users](/intl.en-US/Security Settings/Passwords/Set a password policy for RAM users.md).

    -   **Programmatic Access**: If you select this access mode, an AccessKey pair is automatically created for the RAM user. The RAM user can call API operations or use SDKs to access Alibaba Cloud resources.
    **Note:** To ensure the security of your Alibaba Cloud account, we recommend that you select only one access mode for the RAM user. This prevents the RAM user from using an AccessKey pair to access Alibaba Cloud resources after the RAM user leaves the organization.

6.  Click **OK**.


-   You can attach one or more policies to the RAM user. In this way, you grant the RAM user the access to the Alibaba Cloud resources that are specified in the policies. For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).
-   The RAM user can be used to log on to the console. For more information, see [Log on to the console as a RAM user](/intl.en-US/RAM User Management/Log on to the console as a RAM user.md).
-   You can add the RAM user to one or more RAM user groups and grant permissions to the RAM user groups. For more information, see [Add a RAM user to a RAM user group](/intl.en-US/RAM User Group Management/Add a RAM user to a RAM user group.md).

**Related topics**  


[CreateUser](/intl.en-US/API Reference (RAM)/User management APIs/CreateUser.md)

