# 存在RAM资源导致无法注销阿里云账号的问题

注销阿里云账号前，需要删除该阿里云账号下的全部RAM资源。否则，会注销失败。

-   对于已经通过实名认证的阿里云账号，您可以通过[RAM控制台](https://ram.console.aliyun.com/)或API，按以下操作删除账号下的自定义资源。
    -   删除全部RAM用户。

        具体操作，请参见[删除RAM用户](/intl.zh-CN/用户管理/删除RAM用户.md)。

    -   删除全部RAM用户组。

        具体操作，请参见[删除用户组](/intl.zh-CN/用户组管理/删除用户组.md)。

    -   删除全部RAM角色。

        具体操作，请参见[删除RAM角色](/intl.zh-CN/角色管理/删除RAM角色.md)。

    -   删除全部自定义策略。

        具体操作，请参见[删除自定义策略](/intl.zh-CN/权限策略管理/自定义策略/删除自定义策略.md)。

    -   删除全部身份提供商。

        具体操作，请参见[删除身份提供商](/intl.zh-CN/单点登录管理（SSO）/角色SSO/身份提供商/删除身份提供商.md)。

    -   删除全部虚拟MFA设备。

        正常情况下，删除RAM用户时会同步删除该RAM用户绑定的虚拟MFA设备。但存在以下两种例外情况：

        -   通过RAM控制台为RAM用户启用虚拟MFA时，当进入了绑定虚拟MFA设备的页面（包括RAM管理员为RAM用户绑定和RAM用户自主绑定），但一直未完成绑定的情况下，会产生额外的虚拟MFA设备。
        -   通过[CreateVirtualMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/CreateVirtualMFADevice.md) API创建了虚拟MFA设备，但未绑定RAM用户。
        对于以上的例外情况，您可以先调用[ListVirtualMFADevices](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/ListVirtualMFADevices.md) API查询阿里云账号下存在的所有虚拟MFA设备，然后调用[DeleteVirtualMFADevice](/intl.zh-CN/API参考/API 参考（IMS）/用户管理/DeleteVirtualMFADevice.md) API删除这些虚拟MFA设备。

    -   删除自定义的默认域名名称，将其修改为默认的账号ID。
        1.  查看账号ID。

            当您登录阿里云控制台后，您可以将鼠标悬停在右上角头像的位置，然后单击**安全设置**，查看账号ID。

        2.  修改默认域名名称为账号ID。

            具体操作，请参见[管理默认域名](/intl.zh-CN/安全设置/高级设置/管理默认域名.md)。

-   对于未通过实名认证的阿里云账号，原则上不能使用RAM。但因为一些跨服务授权场景可能导致该阿里云账号下实际存在RAM服务角色，您可以通过API或CLI删除该服务角色。

    下面以在 [Cloudshell](https://shell.aliyun.com/) 中的操作为例。

    1.  执行以下命令，查询账号下的RAM服务角色。

        ```
        aliyun ram ListRoles
        ```

    2.  检查待删除的RAM服务角色是否为[服务关联角色](/intl.zh-CN/角色管理/服务关联角色.md)。

        以“AliyunServiceRoleFor”开头的角色为服务关联角色，其余情况均为普通服务角色。

    3.  删除RAM服务角色。
        -   对于服务关联角色，请按以下步骤进行删除。
            1.  执行以下命令，删除服务关联角色。

                ```
                aliyun resourcemanager DeleteServiceLinkedRole --secure --force --RoleName $role_name
                ```

                将`$role_name`替换为实际的角色名称。

            2.  执行以下命令，查看删除是否成功。

                ```
                aliyun resourcemanager GetServiceLinkedRoleDeletionStatus --DeletionTaskId $task_id
                ```

                将`$task_id`替换为上一步返回的`DeletionTaskId`。如果返回的`Status`为`SUCCEEDED`，表示删除成功。

        -   对于普通服务角色，请执行以下命令进行删除。

            ```
            aliyun ram DeleteRole --secure --force --RoleName $role_name --CascadingDelete true
            ```

            将`$role_name`替换为实际的角色名称。

    4.  再次执行以下命令，查询账号下的全部RAM服务角色是否已被成功删除。

        ```
        aliyun ram ListRoles
        ```


