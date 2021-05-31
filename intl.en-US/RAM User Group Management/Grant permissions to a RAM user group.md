# Grant permissions to a RAM user group

If you grant permissions to a RAM user group, all RAM users in the group share the permissions. This topic describes how to grant permissions to a RAM user group.

## Method 1: Grant permissions to a RAM user group on the Groups page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Groups**.

3.  On the **Groups** page, find the RAM user group to which you want to grant permissions. Click **Add Permissions** in the **Actions** column.

4.  In the Add Permissions panel, grant permissions to the RAM user group.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM user group to which permissions are granted. By default, the current RAM user group is specified. You can also specify another RAM user group.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


## Method 2: Grant permissions to a RAM user group on the Grants page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Permissions** \> **Grants**.

3.  On the Grants page, click **Grant Permission**.

4.  In the Add Permissions panel, grant permissions to a RAM user group.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM user group to which permissions are granted.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


**Related topics**  


[AttachPolicyToGroup](/intl.en-US/API Reference/API Reference (RAM)/Policy management APIs/AttachPolicyToGroup.md)

