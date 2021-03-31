# Disable an MFA device for a RAM user

If you no longer require a multi-factor authentication \(MFA\) device enabled for a RAM user, or you want to change the type of the MFA device that is bound to a RAM user, you can disable the MFA device for the RAM user by using your Alibaba Cloud account or the RAM user who has administrative rights.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account or a RAM user who administrative rights.

    **Note:** If you allow the RAM user of your Alibaba Cloud account to manage its own MFA device, you can disable an MFA device for the RAM user in the RAM console. To disable an MFA device, perform the following operations: Move the pointer over the profile picture in the upper-right corner of the console and click **Security Information Management**. On the **Virtual MFA Device** tab of the Security Management page, click **Disable Virtual MFA Device**. You can also click **Disable U2F Security Key** on the **U2F Security Key** tab.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  In the **User Logon Name/Display Name** column, click the username of the RAM user for which you want to disable an MFA device.

4.  In the page that appears, click the **Authentication** tab.

    -   On the tab, click the **Virtual MFA Device** tab and click **Disable Virtual MFA Device**. The virtual MFA device is disabled.
    -   On the tab, click the **U2F Security Key** tab and click **Disable U2F Security Key**. The U2F security key is disabled.
5.  Click **OK**.


**Related topics**  


[UnbindMFADevice](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/UnbindMFADevice.md)

