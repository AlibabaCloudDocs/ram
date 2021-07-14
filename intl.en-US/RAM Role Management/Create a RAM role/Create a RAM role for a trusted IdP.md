# Create a RAM role for a trusted IdP

This topic describes how to create a Resource Access Management \(RAM\) role for a trusted identity provider \(IdP\). This type of RAM role is used to implement single sign-on \(SSO\) between Alibaba Cloud and a trusted IdP.

An IdP is created. For more information, see [Create an IdP](/intl.en-US/SSO Management/Role-based SSO/Identity providers/Create an IdP.md).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role panel, select **IdP** for Trusted entity type and click **Next**.

5.  Specify the **RAM Role Name** and **Note** parameters.

6.  Select a trusted IdP, view the conditions, and then click **OK**.

    **Note:** Only the `saml:recipient` condition key is supported. This condition key is required and cannot be changed.


After you create a RAM role, the RAM role has no permissions. You can grant permissions to the RAM role. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

**Related topics**  


[CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md)

