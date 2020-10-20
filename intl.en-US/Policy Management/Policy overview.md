# Policy overview

This topic describes the permissions and policies of Alibaba Cloud. To grant different permissions to Resource Access Management \(RAM\) identities on Alibaba Cloud resources, you can attach different policies to the RAM identities.

## Permission

Permissions are specified by a statement within a policy that allows or denies access to a specific Alibaba Cloud resource.

-   An Alibaba Cloud account is the resource owner and controls all permissions.
    -   Each Alibaba Cloud resource has only one owner. The owner must be an Alibaba Cloud account and has complete control over the resource.
    -   The resource owner is not necessarily the resource creator. For example, if a RAM user has permission to create Alibaba Cloud resources, the resources created by this RAM user belong to the Alibaba Cloud account of the RAM user. The RAM user is the resource creator, but is not the resource owner.
-   A RAM user has no permissions by default.
    -   A RAM user is an identity that is used to manage resources. Before a RAM user can perform operations, the RAM user must be granted the required permissions by the Alibaba Cloud account. The required permissions must be granted by attaching one or more explicit allow policies.
    -   A new RAM user can manage resources only after the RAM user is granted the required permissions.
-   As a resource creator, a RAM user is not automatically granted the permissions on the created resources.
    -   A RAM user can create resources after the RAM user is granted the required permissions.
    -   To grant the RAM user the required permissions, the resource owner must attach one or more explicit allow policies to the RAM user.

## Policy

A policy defines a set of permissions that are described based on the policy structure and syntax. A policy can accurately describe the authorized resource sets, authorized operation sets, and authorization conditions. For more information, see [Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md).

In RAM, a policy is a resource entity that can be created, updated, deleted, and viewed. RAM supports the following two types of policies:

-   **System Policy**: System policies are automatically created and upgraded by Alibaba Cloud and cannot be modified by users.
-   **Custom Policy**: Custom policies are created, modified, and deleted by users to meet their business requirements.

You can attach one or more policies to RAM users, RAM user groups, or RAM roles. For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md), [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md) and [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

## Policies attached to RAM identities

You can attach one or more policies to RAM identities to grant the identities the relevant permissions.

-   The attached policies can be system policies or custom policies.
-   If the attached policies are modified, the new policies automatically take effect. You do not need to attach the new policies to RAM identities.

