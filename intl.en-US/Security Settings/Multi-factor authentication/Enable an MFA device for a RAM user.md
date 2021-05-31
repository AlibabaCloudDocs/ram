# Enable an MFA device for a RAM user

This topic describes how to enable a multi-factor authentication \(MFA\) device for a Resource Access Management \(RAM\) user. Virtual MFA devices and Universal 2nd Factor \(U2F\) security keys are two types of MFA devices. After you enable an MFA device, it provides higher security protection for your Alibaba Cloud account.

**Note:** You can enable only one type of the MFA device for a RAM user.

## Enable a virtual MFA device

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account or a RAM user that has administrative rights.

    **Note:**

    -   If you selected Required for Enable MFA when you modified the logon settings of RAM users, you are required to bind an MFA device upon logon. You can select **Virtual MFA Device** in the Enable MFA Device dialog box and go to Step 6.
    -   If you allow the RAM user of your Alibaba Cloud account to manage its own MFA device, you can enable an MFA device for the RAM user in the RAM console. To enable an MFA device, perform the following operations: Move the pointer over the profile picture in the upper-right corner of the console and click **Security Information Management**. On the **Virtual MFA Device** tab of the Security Management page, click **Enable Virtual MFA Device**.
2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the username of the RAM user for which you want to enable a virtual MFA device.

4.  On the page that appears, click the **Authentication** tab. Then, click the **Virtual MFA Device** tab.

5.  Click **Enable the Virtual MFA Device**.

6.  Download and install the Google Authenticator app on your mobile phone.

    -   For iOS, download the Google Authenticator app from the App Store.
    -   For Android, download the Google Authenticator app from the Google Play Store.

        **Note:** For Android, you must install a quick response \(QR\) code scanner from the Google Play Store for Google Authenticator to identify QR codes.

7.  Open the Google Authenticator app and tap BEGIN SETUP.

8.  Select a method to enable the MFA device from the following available options:

    -   Tap **Scan barcode** in the Google Authenticator app and scan the QR code that is displayed on the **Scan the code.** tab in the RAM console. This option is recommended.
    -   Tap **Manual entry**, enter the username and key, and then tap the **√** icon in the Google Authenticator app.

        **Note:** You can obtain the username and key from the **Retrieve manually enter information.** tab in the RAM console.

9.  Enter the two consecutive verification codes that are displayed on the Google Authenticator app. Then, click **Enable**.

    **Note:** Verification codes in the Google Authenticator app are updated at an interval of 30 seconds.


## Enable a U2F security key

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account or a RAM user that has administrative rights.

    **Note:**

    -   If you have selected Required for Enable MFA when you modify the logon settings of RAM users, you are required to bind an MFA device upon logon. You can select U2F Security Key in the **Enable MFA Device** dialog box and go to Step 6.
    -   If you allow the RAM user of your Alibaba Cloud account to manage its own MFA device, you can enable an MFA device for the RAM user in the RAM console. To enable an MFA device, perform the following operations: Move the pointer over the profile picture in the upper-right corner of the console and click **Security Information Management**. On the **U2F Security Key** tab of the Security Management page, click **Enable U2F Security Key**.
2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the username of the RAM user for which you want to enable a virtual MFA device.

4.  On the page that appears, click the **Authentication** tab. Then, click the **U2F Security Key** tab.

5.  Click **Enable U2F Security Key**.

6.  On the Bind U2F Security Key page, bind the RAM user to the U2F security key.

    **Note:** Before you perform the following operations, you must understand the limits on U2F security keys. For more information, see [Limits on U2F security keys](/intl.en-US/Security Settings/Overview of security settings.md).

    1.  Plug the U2F security key into the USB port on your computer.

    2.  Tap the button of the U2F security key.

    3.  In the message that prompts you to obtain the U2F security key, click **OK**.

    4.  In the message indicating that the U2F security key is obtained, click **Confirm**.


After you enable the MFA device and use the RAM user to log on the Alibaba Cloud Management Console again, the RAM console prompts you to perform the following operations:

1.  Enter the username and password of the RAM user.
2.  Enter the verification code that is generated by the virtual MFA device, or pass U2F authentication.

**Note:**

-   If you want to change the type of the MFA device that is bound to a RAM user, you must log on to the RAM console, disable the MFA device, and then bind the RAM user to another MFA device. For more information, see [Disable an MFA device](/intl.en-US/Security Settings/Multi-factor authentication/Disable an MFA device for a RAM user.md).
-   If you uninstall the virtual MFA device before you disable the MFA device, or your U2F security key is lost, you cannot log on to the Alibaba Cloud Management Console. If this happens, you must use your Alibaba Cloud account or the RAM user that has administrative rights to log on to the RAM console and disable the MFA device. Then, bind the RAM user to another MFA device. For more information, see [Disable an MFA device](/intl.en-US/Security Settings/Multi-factor authentication/Disable an MFA device for a RAM user.md).

**Related topics**  


[BindMFADevice](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/BindMFADevice.md)

