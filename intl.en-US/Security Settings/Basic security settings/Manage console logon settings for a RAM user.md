# Manage console logon settings for a RAM user

This topic describes how to enable console logon and modify or clear console logon settings for a Resource Access Management \(RAM\) user.

## Enable console logon for a RAM user

You can enable console logon for a RAM user and configure parameters such as the logon password.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the name of the RAM user.

4.  In the **Console Logon Management** section of the **Authentication** tab, click **Enable Console Logon**.

5.  In the Modify Logon Settings panel, configure the following parameters.

    -   **Console Password Logon**: Click **Enabled**.
    -   **Set Logon Password**: Select Automatically Generate Default Password or Custom Logon Password based on your business requirements.

        **Note:** We recommend that you record the password for subsequent use.

    -   **Password Reset**: Set this parameter to specify whether to reset the password upon the next logon of the RAM user.
    -   **Enable MFA**: Set this parameter to specify whether to enable multi-factor authentication \(MFA\) for the RAM user.

        **Note:** If you select Required, the page on which you can enable an MFA device automatically appears upon the next logon of the RAM user.

6.  Click **OK**.


## Modify console logon settings for a RAM user

After you enable console logon for a RAM user, you can modify console logon settings based on your business requirements. For example, you can disable console logon or modify the logon password.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the name of the RAM user.

4.  In the **Console Logon Management** section of the **Authentication** tab, click **Modify Logon Settings**.

5.  In the Modify Logon Settings panel, configure the following parameters.

    -   **Console Password Logon**: Click **Disabled**.

        **Note:** If you select Disabled, you can still modify logon settings for the RAM user. However, the settings that you modify do not take effect. The settings take effect only after you click **Enabled**.

    -   **Set Logon Password**: Select Automatically Generate Default Password or Custom Logon Password based on your business requirements.

        **Note:** We recommend that you record the password for subsequent use.

    -   **Password Reset**: Set this parameter to specify whether to reset the password upon the next logon of the RAM user.
    -   **Enable MFA**: Set this parameter to specify whether to enable multi-factor authentication \(MFA\) for the RAM user.

        **Note:** If you select Required, the page on which you can enable an MFA device automatically appears upon the next logon of the RAM user.

6.  Click **OK**.


## Clear console logon settings for a RAM user

You can clear console logon settings for a RAM user with a few clicks and disable console logon for the RAM user.

**Note:** The console logon settings cannot be automatically restored after the settings are cleared. Proceed with caution.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the name of the RAM user.

4.  In the **Console Logon Management** section of the **Authentication** tab, click **Clear Logon Settings**.

5.  In the Clear Logon Settings panel, click **OK**.


