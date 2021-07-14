# Remove permissions from a RAM role

If a Resource Access Management \(RAM\) role no longer needs specific permissions, you can remove the permissions from the RAM role. This topic describes how to remove the permissions from a RAM role.

**Note:** You cannot remove permissions from service-linked roles by detaching policies from the roles. This is because the policies that are attached to this type of role are defined by the linked cloud services. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Method 1: Remove permissions from a RAM role on the RAM Roles page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, find the specific RAM role and click its name.

4.  On the page that appears, click the **Permissions** tab, find the specific policies that you want to detach from the RAM role, and then click **Remove Permission** in the **Actions** column.

5.  Click **OK**.


## Method 2: Remove permissions from a RAM role on the Grants page

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Permissions** \> **Grants**.

3.  On the Users page, find the RAM role from which you want to remove permissions and click **Revoke Permission** in the **Actions** column.

4.  Click **OK**.


**Related topics**  


[DetachPolicyFromRole](/intl.en-US/API Reference/API Reference (RAM)/Policy management APIs/DetachPolicyFromRole.md)

