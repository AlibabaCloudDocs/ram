# Set the maximum session duration for a RAM role

This topic describes how to use the console or API to set the maximum session duration for a RAM role. If you set the maximum session duration to a large value for a RAM role, RAM users can assume the RAM role to complete time-consuming tasks. If the RAM users call an STS API operation to assume the RAM role, the STS tokens that are returned have a long validity period.

-   The maximum session duration for a RAM role ranges from 3,600 seconds to 43,200 seconds. The default maximum session duration is 3,600 seconds.
-   The maximum session duration of service linked roles is not configurable.

## Use the console to set the maximum session duration for a RAM role

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the **RAM Roles** page, click the name of a RAM role in the **RAM Role Name** column.

4.  In the **Basic Information** section, click **Edit** next to **Maximum Session Duration**.

5.  In the dialog box that appears, modify the maximum session duration and click **OK**.


## Call an API operation to set the maximum session duration for a RAM role

You can set the MaxSessionDuration or NewMaxSessionDuration parameter when you call the CreateRole or UpdateRole operation. For more information, see [CreateRole](/intl.en-US/API Reference (RAM)/Role management APIs/CreateRole.md) and [UpdateRole](/intl.en-US/API Reference (RAM)/Role management APIs/UpdateRole.md).

After you set the maximum session duration for a RAM role, you can use the console or an STS API operation to assume the RAM role.You can also use the RAM role for role-based single sign-on \(SSO\). For more information, see the following topics:

-   [Assume a RAM role](/intl.en-US/RAM Role Management/Assume a RAM role.md)
-   [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md)
-   [AssumeRole](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md)
-   [AssumeRoleWithSAML](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md)

