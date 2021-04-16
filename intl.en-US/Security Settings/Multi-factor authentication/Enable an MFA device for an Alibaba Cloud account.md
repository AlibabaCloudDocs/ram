# Enable an MFA device for an Alibaba Cloud account

This topic takes the Google Authenticator app as an example to describe how to enable a multi-factor authentication \(MFA\) device for an Alibaba Cloud account.After an MFA device is enabled, it provides additional security protection for your Alibaba Cloud account.

## Procedure

1.  Log on to the Alibaba Cloud consoleAlibaba Cloud console by using your Alibaba Cloud account.

2.  Move the pointer over the profile picture in the upper-right corner of the console, and click Security Settings.

3.  In the Account Protection section of the Security Settings page, click Edit.

    **Note:** MFA has been renamed TOTP.

4.  On the Turn on Account Protection page, select scenarios and the TOTP verification method, and then click Submit.

5.  In the Verify identity step of the Identity Verification page, select a verification method.

6.  Click Verify now, enter the verification code, and then click Submit.

7.  Download and install Google Authenticator on your mobile phone. After you install Google Authenticator, go back to the Install the application step on the Identity Verification page and click Next.

    -   For iOS, install the Google Authenticator app from the App Store.
    -   For Android, install the Google Authenticator app from the Google Play Store.

        **Note:** For Android, you must install a QR code scanner from the Google Play Store for Google Authenticator to identify QR codes.

8.  Open the Google Authenticator app.

9.  Select a method to enable the MFA device from the following available options.

    -   \(Recommended\) Tap Scan barcode in the Google Authenticator app, and scan the QR code in the Enable the MFA step on the Identity Verification page in the Alibaba Cloud Management Console.
    -   Tap Manual entry, enter the username and key, and then tap the √ icon in the Google Authenticator app.

        **Note:** You can find the username and key by moving the pointer over Scan failed in the Enable the MFA step of the Identity Verification page.

10. In the Enable the MFA step of the Identity Verification page, enter the dynamic verification code in the Google Authenticator app, and click Next to complete the account protection settings.

    **Note:** The verification code in the Google Authenticator app is refreshed every 30 seconds.


After you enable the MFA device and use the Alibaba Cloud account to log on to the RAM console again, you are prompted to enter the following verification information:

1.  Username and password of the Alibaba Cloud account.
2.  Verification code provided by the MFA device

**Note:**

-   The MFA device enabled for your Alibaba Cloud account do not affect the logon of your RAM users.
-   Before you uninstall or remove an MFA device, you must log on to the Alibaba Cloud Management Console and disable the MFA device. Otherwise, a logon failure may occur.

**Related topics**  


[BindMFADevice](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/BindMFADevice.md)

