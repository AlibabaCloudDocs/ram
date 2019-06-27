# Create a RAM role for a trusted IdP {#task_221537 .task}

This topic describes how to create a RAM role for a trusted identity provider \(IdP\). You can create a RAM role for three types of trusted entities: trusted Alibaba Cloud accounts, trusted Alibaba Cloud services, and trusted IdPs.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click **RAM Roles**.
3.  Click **Create RAM Role**.
4.  Select **IdP** and click **Next**.
5.  Enter a RAM role name and description.
6.  Select a trusted IdP and click **OK**. 

    **Note:** In the **Condition Keyword** column, only the keyword `saml:recipient` \(which is required and cannot be modified\) is currently allowed.


After you create a RAM role, you can click **Add Permissions to RAM Role** to grant permission to this role. For more information, see [Grant permission to a RAM role](intl.en-US/User Guide/RAM roles/Grant permission to a RAM role.md#).
