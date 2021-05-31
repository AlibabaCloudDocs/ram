# Grant permissions to a RAM role

You can grant permissions to a RAM role that you have created for a trusted Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\). This topic describes how to grant permissions to a RAM role.

**Note:** You cannot grant permissions to a service-linked role because the policy that is attached to the role is predefined by the linked cloud service. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Method 1: Grant permissions to a RAM role by clicking Add Permissions on the RAM Roles page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, find the RAM role to which you want to grant permissions. Click **Add Permissions** in the **Actions** column.

4.  In the Add Permissions panel, grant permissions to the RAM role.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM role to which permissions are granted. By default, the current RAM role is specified. You can also specify another RAM role.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


## Method 2: Grant permissions to a RAM role by clicking Input and Attach on the RAM Roles page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, find the RAM role to which you want to grant permissions. Click **Input and Attach** in the **Actions** column.

4.  In the Add Permissions panel, set Type to **System Policy** or **Custom Policy**, and enter a policy name.

5.  Click **OK**.

6.  Click **Close**.


## Method 3: Grant permissions to a RAM role on the Grants page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Permissions** \> **Grants**.

3.  On the Grants page, click **Grant Permission**.

4.  In the Add Permissions panel, grant permissions to a RAM role.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM user to which permissions are granted.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


**Related topics**  


[AttachPolicyToRole](/intl.en-US/API Reference/API Reference (RAM)/Policy management APIs/AttachPolicyToRole.md)

