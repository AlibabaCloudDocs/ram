# Grant permissions to a RAM user

A RAM user can access Alibaba Cloud resources after it is granted the relevant permissions. This topic describes how to grant permissions to a RAM user.

## Method 1: Grant permissions to a RAM user on the User page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, find the RAM user to which you want to grant permissions. Click **Add Permissions** in the **Actions** column.

4.  In the Add Permissions panel, grant permissions to the RAM user.

    1.  Select the authorization scope.

        -   **Alibaba Cloud Account**: Permissions take effect on the current Alibaba Cloud account.
        -   **Specific Resource Group**: Permissions take effect on a specific resource group.

            **Note:** If you select Specific Resource Group as the authorization scope, you must make sure that the cloud service supports resource groups. For more information, see [Alibaba Cloud services that support resource groups]().

    2.  Specify the principal.

        The principal is the RAM user to which permissions are granted. By default, the current RAM user is specified. You can also specify another RAM user.

    3.  Select policies.

        **Note:** You can bind a maximum of five policies to a RAM user at a time. If you need to bind more than five policies to a RAM user, perform the bind operation multiple times.

5.  Click **OK**.

6.  Click **Complete**.


## Method 2: Grant permissions to a RAM user on the Grants page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Permissions** \> **Grants**.

3.  On the Grants page, click **Grant Permission**.

4.  In the Add Permissions panel, grant permissions to a RAM user.

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


[AttachPolicyToUser](/intl.en-US/API Reference/API Reference (RAM)/Policy management APIs/AttachPolicyToUser.md)

