# Configure the password policy for RAM users

This topic describes how to configure the password policy for the RAM users of your Alibaba Cloud account. You can specify password complexity requirements, including the password length, validity period, and password history check.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Settings**.

3.  On the **Security Settings** tab of the page that appears, click **Edit Password Rule**. In the panel that appears, configure the parameters.

    -   **Password Length**: The password must be 8 to 32 characters in length.

        **Note:** To ensure account security, the password must be at least eight characters in length.

    -   **Required Elements in Password**: The available elements include Lowercase Letters, Uppercase Letter, Numbers, and Symbols.

        **Note:** To enhance account security, we recommend that you select at least two of the preceding elements.

    -   **Minimum Different Characters in Password**: The value ranges from 0 to 8. The default value is 0, which indicates that no limits are imposed on the number of unique characters in a password.
    -   **Include Username in Password**: Select **Allow** or **Do Not Allow** as needed.
        -   **Allow**: A password can contain the username.
        -   **Do Not Allow**: A password cannot contain the username.
    -   **Password Validity Period**: The value ranges from 0 to 1095, in days. The default value is 0, which indicates that the password never expires.

        **Note:** The password validity period restarts if you reset the password.

    -   **Action After Password Expires**: You can specify whether to allow the RAM users to log on to the console after their passwords expire. You can select **Deny Logon** or **Allow Logon** as needed.
        -   **Deny Logon**: After the password expires, you cannot use the password to log on to the console. You can log on to the console only after you reset the password by using your Alibaba Cloud account or as a RAM user that has administrative rights.
        -   **Allow Logon**: After the password expires, you can change the password to log on to the console.
    -   **Password History Check Policy**: You can prevent RAM users from reusing the previous N passwords. The value ranges from 0 to 24. The default value is 0, which indicates that the RAM users can reuse previous passwords.
    -   **Password Retry Constraint Policy**: This parameter specifies the maximum number of password retries. If you enter the wrong passwords for the specified consecutive times, the account is locked for one hour. The value ranges from 0 to 32. The default value is 0, which indicates that the password retries are not limited.

        **Note:** After you change the password, the number of password retries is reset to zero.

4.  Click **OK**.


The password policy applies to all RAM users of your Alibaba Cloud account.

**Related topics**  


[SetPasswordPolicy](/intl.en-US/API Reference/API Reference (RAM)/Security management APIs/SetPasswordPolicy.md)

