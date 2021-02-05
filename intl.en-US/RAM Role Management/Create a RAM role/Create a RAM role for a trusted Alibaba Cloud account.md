# Create a RAM role for a trusted Alibaba Cloud account

You can create RAM roles for three types of trusted entity: Alibaba Cloud account, Alibaba Cloud service, and identity provider \(IdP\). This topic describes how to create a RAM role for a trusted Alibaba Cloud account.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role pane, set the Trusted Entity Type parameter to **Alibaba Cloud Account**, and then click **Next**.

5.  Specify the **RAM Role Name** and **Note** parameters.

6.  Select **Current Alibaba Cloud Account** in the Select Trusted Alibaba Cloud Account field and click **OK**.

    **Note:** If you select **Other Alibaba Cloud Account**, you must enter the ID of the Alibaba Cloud account.


After you create a RAM role, the RAM role has no permissions by default. You can click **Add Permissions to RAM Role** to grant permissions to the RAM role. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

**Related topics**  


[CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md)

