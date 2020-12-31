# Use a RAM role to grant permissions across Alibaba Cloud accounts

This topic describe how to use a Resource Access Management \(RAM\) role to grant permissions across Alibaba Cloud accounts. Two enterprises \(Enterprise A and Enterprise B\) are used as examples. To authorize Enterprise B to access specified resources of Enterprise A, Enterprise A can create and assign a RAM role to Enterprise B. Then, Enterprise B can assume the RAM role and access the specified resources.

An alias is set for your Alibaba Cloud account. For more information, see [Manage the default domain name](/intl.en-US/Security Settings/Advanced settings/Manage the default domain name.md).

An enterprise \(Enterprise A\) has purchased multiple types of Alibaba Cloud resources, such as ECS instances, RDS instances, SLB instances, and OSS buckets. Enterprise A wants to authorize Enterprise B to access specified resources of Enterprise A.

Enterprise A has the following requirements:

-   Enterprise A only serves as a cloud resource owner. Enterprise A can authorize Enterprise B to maintain, monitor, and manage specified cloud resources of Enterprise A.
-   If an employee joins or leaves Enterprise B, Enterprise B does not need to change permissions. Enterprise B can grant fine-grained permissions on cloud resources of Enterprise A to its RAM users \(employees or applications\).
-   If the agreement between Enterprise A and Enterprise B ends, Enterprise A can revoke the permissions from Enterprise B based on business requirements.

## Solution

In this example, Enterprise A needs to authorize employees of Enterprise B to manage ECS resources of Enterprise A. Enterprise A has an Alibaba Cloud account named Account A and Enterprise B has an Alibaba Cloud account named Account B.

-   The ID of Account A is `123456789012****` and the account alias is `company-a`.
-   The ID of Account B is `134567890123****` and the account alias is `company-b`.

1.  Enterprise A uses Account A to create a RAM role, grants the required permissions to the RAM role, and then authorizes Account B to assume this role.

    For more information, see [Grant permissions across Alibaba Cloud accounts](#section_04).

2.  If an employee \(a RAM user\) under Account B needs to assume this role, Account B can grant the required permissions to the RAM user. Then, the RAM user assumes the RAM role to access the resources of Account A.

    For more information, see [Access resources across Alibaba Cloud accounts](#section_05).

3.  If the agreement between Enterprise A and Enterprise B ends, Enterprise A can revoke the permissions from Account B. Then, all RAM users of Account B no longer have the permissions of the RAM role.

    For more information, see [Revoke permissions across Alibaba Cloud accounts](#section_06).


## Grant permissions across Alibaba Cloud accounts

1.  Enterprise A uses Account A to create a RAM role named `ecs-admin`. **Alibaba Cloud Account** is selected as the trusted entity type.

    **Note:** When the RAM role is created, **Other Alibaba Cloud Account** is selected and `134567890123****` is specified as the trusted Alibaba Cloud account. This ensures that RAM users under Account B can assume the RAM role.

    For more information, see [Create a RAM role for a trusted Alibaba Cloud account](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud account.md).

    After the RAM role is created, Enterprise A can view information about the RAM role on the basic information page.

    -   In this example, the Alibaba Cloud Resource Name \(ARN\) of the RAM role is `acs:ram::123456789012****:role/ecs-admin`.
    -   The following policy is attached to the RAM role:

        **Note:** This policy indicates that RAM users of Account B can assume the RAM role.

        ```
        {
        "Statement": [
        {
         "Action": "sts:AssumeRole",
         "Effect": "Allow",
         "Principal": {
           "RAM": [
             "acs:ram::134567890123****:root"
           ]
         }
        }
        ],
        "Version": "1"
        }
        ```

2.  Enterprise A uses Account A to attach the `AliyunECSFullAccess` policy to the RAM role `ecs-admin`.

    For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

3.  Enterprise B uses Account B to create a RAM user named `Alice`.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

4.  Enterprise B uses Account B to set the logon password of the RAM user to `123456****` and attach the `AliyunSTSAssumeRoleAccess` system policy to the RAM user. This allows the RAM user to assume the RAM role.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).


## Access resources across Alibaba Cloud accounts

After Enterprise A uses Account A to grant required permissions to Account B, the RAM user `Alice` of Account B can access ECS resources of Account A by assuming the RAM role. An employee of Enterprise B can perform the following steps to assume the RAM role as a RAM user:

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) as the RAM user named Alice.

    **Note:** On the logon page, you must enter the account alias `company-b`, username `Alice`, and password `123456****`.

    For more information, see [Log on to the console as a RAM user](/intl.en-US/RAM User Management/Log on to the console as a RAM user.md).

2.  Move the pointer over the profile picture and click **Switch Role**.

    **Note:** On the page that appears, you must enter the account alias `company-a` and role name `ecs-admin`.

    For more information, see [Assume a RAM role](/intl.en-US/RAM Role Management/Assume a RAM role.md).


## Revoke permissions across Alibaba Cloud accounts

Enterprise A can use Account A to revoke the permission to assume the RAM role `ecs-admin` from Account B. Enterprise A can perform the following steps to revoke the permission to assume the RAM role:

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with Account A.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  In the RAM Role Name column, click the RAM role `ecs-admin`.

4.  On the **Trust Policy Management** tab, click **Edit Trust Policy**. In the pane that appears, delete `"acs:ram::134567890123****:root"`.

    **Note:** Enterprise A can also use Account A to delete the RAM role **ecs-admin**. This revokes the permissions of the RAM role from Account B. Before the RAM role is deleted, the policies attached to the RAM role must be detached. For more information, see [Remove permissions from a RAM role](/intl.en-US/RAM Role Management/Remove permissions from a RAM role.md).


