# Specify the maximum session duration for a RAM role

This topic describes how to use the console or API to specify the maximum session duration for a Resource Access Management \(RAM\) role. If you set the maximum session duration to a large value for a RAM role, RAM users can assume the RAM role to complete time-consuming tasks. If the RAM users call a Security Token Service \(STS\) operation to assume the RAM role, the STS tokens that are returned have a long validity period.

-   Valid values of the maximum session duration for a RAM role: 3600 to 43200. Unit: seconds. Default value of the maximum session duration: 3600. Unit: seconds.
-   The maximum session duration of service-linked roles is not configurable.

## Use the console to specify the maximum session duration for a RAM role

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, find the specific RAM role and click its name.

4.  In the **Basic Information** section, click **Edit** to the right of **Maximum Session Duration**.

5.  In the dialog box that appears, change the maximum session duration and click **OK**.


## Call an operation to specify the maximum session duration for a RAM role

When you call the CreateRole or UpdateRole operation, you can configure the MaxSessionDuration or NewMaxSessionDuration parameter. For more information, see [CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md) and [UpdateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/UpdateRole.md).

After you configure the maximum session duration for a RAM role, you can use the console or an STS operation to assume the RAM role.You can also use the RAM role for role-based single sign-on \(SSO\). For more information, see the following topics:

-   [Assume a RAM role](/intl.en-US/RAM Role Management/Assume a RAM role.md)
-   [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md)
-   [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md)
-   [AssumeRoleWithSAML](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md)

