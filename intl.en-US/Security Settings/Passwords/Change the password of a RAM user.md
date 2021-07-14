# Change the password of a RAM user

This topic describes how to change the password of a Resource Access Management \(RAM\) user that belongs to your Alibaba Cloud account. You can change your password on a regular basis for account security.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, find the specific RAM user and click its name.

4.  On the **Authentication** tab of the user details page, click **Modify Logon Settings**.

5.  In the **Set Logon Password** section of the Modify Logon Settings panel, reset the logon password.

    -   If you select **Keep Current Password Unchanged**, the password remains unchanged.
    -   If you select **Automatically Regenerate Default Password** and click **OK**, the system generates a logon password. You must save the generated password for subsequent use.
    -   If you select **Reset Custom Password**, enter a new password and click **OK**.

        **Note:** The new password must meet the complexity requirements. For more information, see [Configure the password policy for RAM users](/intl.en-US/Security Settings/Passwords/Configure the password policy for RAM users.md).

6.  Click **Close**.

    **Note:** If your Alibaba Cloud account allows RAM users to manage their passwords, the RAM users can change their passwords in the console.


**Related topics**  


[ChangePassword](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/ChangePassword.md)

