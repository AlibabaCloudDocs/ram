# What can I do if I fail to close my Alibaba Cloud account?

Before you close an Alibaba Cloud account, you must delete all the Resource Access Management \(RAM\) resources of the Alibaba Cloud account. Otherwise, the Alibaba Cloud account cannot be closed.

-   If your Alibaba Cloud account has passed real-name verification, you can use the [RAM console](https://ram.console.aliyun.com/) or RAM API to delete the custom resources of the account. Perform the following operations:
    -   Delete all RAM users.

        For more information, see [Delete a RAM user](/intl.en-US/RAM User Management/Basic operations/Delete a RAM user.md).

    -   Delete all RAM user groups.

        For more information, see [Delete a RAM user group](/intl.en-US/RAM User Group Management/Delete a RAM user group.md).

    -   Delete all RAM roles.

        For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

    -   Delete all custom policies.

        For more information, see [Delete a custom policy](/intl.en-US/Policy Management/Custom policies/Delete a custom policy.md).

    -   Delete all identity providers \(IdPs\).

        For more information, see [Delete an IdP](/intl.en-US/SSO Management/Role-based SSO/Identity providers/Delete an identity provider.md).

    -   Delete all virtual multi-factor authentication \(MFA\) devices.

        In most cases, when a RAM user is deleted, the virtual MFA device bound to the RAM user is synchronously deleted. However, a virtual MFA device cannot be deleted in the following cases:

        -   You requested to bind a virtual MFA device to a RAM user but the request failed. In this case, additional virtual MFA devices were generated.
        -   You created a virtual MFA device by calling the [CreateVirtualMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateVirtualMFADevice.md) operation but you did not bind it to a RAM user.
        To resolve the issue, you can call the [ListVirtualMFADevices](/intl.en-US/API Reference/API Reference (IMS)/User management/ListVirtualMFADevices.md) operation to query all the virtual MFA devices of the current Alibaba Cloud account. Then, call the [DeleteVirtualMFADevice](/intl.en-US/API Reference/API Reference (IMS)/User management/DeleteVirtualMFADevice.md) operation to delete these virtual MFA devices.

    -   Change the custom default domain name to the default account ID.
        1.  View your account ID

            Log on to the Alibaba Cloud Management Console. In the upper-right corner, move the pointer over the profile and click **Security Settings**. On the Security Settings page, view the account ID.

        2.  Change the default domain name to the account ID.

            For more information, see [Manage the default domain name](/intl.en-US/Security Settings/Advanced settings/Manage the default domain name.md).

-   If your Alibaba Cloud account has not passed real-name verification, you cannot use the RAM service. However, you may have created RAM roles to use other cloud services. In this case, you can use RAM API or the command-line interface \(CLI\) to delete these roles.

    [Alibaba Cloud Shell](https://shell.aliyun.com/) is used as an example to show how to delete RAM roles.

    1.  Run the following command to query the RAM roles of the account:

        ```
        aliyun ram ListRoles
        ```

    2.  Check whether the RAM roles to be deleted are service-linked roles. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

        Roles that start with "AliyunServiceRoleFor" are service-linked roles.

    3.  Deletes RAM roles.
        -   Perform the following steps to delete a service-linked role:
            1.  Run the following command to delete the service-linked role:

                ```
                aliyun resourcemanager DeleteServiceLinkedRole --secure --force --RoleName $role_name
                ```

                Replace `$role_name` with the actual role name.

            2.  Run the following command to check whether the service-linked role is deleted:

                ```
                aliyun resourcemanager GetServiceLinkedRoleDeletionStatus --DeletionTaskId $task_id
                ```

                Replace `$task_id` with `DeletionTaskId` returned in the previous step. If the returned `Status` is `SUCCEEDED`, the service-linked role is deleted.

        -   Run the following command to delete a normal service role:

            ```
            aliyun ram DeleteRole --secure --force --RoleName $role_name --CascadingDelete true
            ```

            Replace `$role_name` with the actual role name.

    4.  Run the following command to check whether all the RAM roles of your account are deleted:

        ```
        aliyun ram ListRoles
        ```


