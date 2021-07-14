# Create a RAM role for a trusted Alibaba Cloud account

This topic describes how to create a Resource Access Management \(RAM\) role for a trusted Alibaba Cloud account. This RAM role is mainly used to solve the issues of cross-account access and temporary authorization. The RAM user that assumes the role can belong to your Alibaba Cloud account or a different Alibaba Cloud account.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role panel, select **Alibaba Cloud Account** for the Trusted entity type parameter and click **Next**.

5.  Specify the **RAM Role Name** and **Note** parameters.

6.  Select **Current Alibaba Cloud Account** for Select Trusted Alibaba Cloud Account field and click **OK**.

    **Note:** If you select **Other Alibaba Cloud Account**, you must enter the ID of another Alibaba Cloud account. You can view the ID of an Alibaba Cloud account on the [Security Settings](https://account-intl.console.aliyun.com/#/secure) page.


After you create a RAM role, the RAM role has no permissions. You can grant permissions to the RAM role. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

**Related topics**  


[CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md)

