# Use RAM to create and authorize resource groups

This topic describes how to use Resource Access Management \(RAM\) to create and authorize resource groups in Alibaba Cloud. After you create and authorize resource groups, you can manage your own members, permissions, and resources by group.

A gaming enterprise is developing three gaming projects. Each project requires various cloud resources. The enterprise has an Alibaba Cloud account and more than 100 Elastic Compute Service \(ECS\) instances that belong to the Alibaba Cloud account.

The enterprise has the following requirements:

-   Independent project management: Project managers can manage their own project members and the permissions that the project members require to access cloud resources.
-   Separate bills: The financial department of the enterprise requires that each project receives separate bills.
-   Shared bottom-layer network: The enterprise requires a shared bottom-layer network for its cloud resources.

The enterprise has the following optional solutions:

-   Multi-account solution
    -   This solution supports independent project management. The enterprise creates three Alibaba Cloud accounts \(one account for each project\) and assigns one project manager for each account. Then, project managers can manage their own project members and access permissions of each member.
    -   This solution supports separate bills. By default, each Alibaba Cloud account receives separate bills. The enterprise can use the consolidated billing feature provided by Alibaba Cloud to consolidate the bills and invoices of the multiple Alibaba Cloud accounts.
    -   This solution does not support a shared bottom-layer network. The resources of different accounts are isolated between different networks. Virtual private clouds \(VPCs\) of the accounts can be connected by using peering connections. However, this leads to higher management costs.
-   Single-account solution \(with tagged resources\)
    -   This solution does not support independent project management. The enterprise can tag its cloud resources by group, but project managers cannot manage their own members and access permissions of each member.
    -   This solution supports separate bills. The enterprise can tag its cloud resources by project. Then, each project can receive separate bills.
    -   This solution supports a shared bottom-layer network. The enterprise can use tag-based RAM policies to authorize RAM users to access a group of resources. These resources belong to the same Alibaba Cloud account, and the enterprise does not need to pay for peering connections.
-   [Resource group-based management solution](#section_03)
    -   This solution supports independent project management. Each resource group has an administrator. Administrators can manage their own group members and access permissions of each member.
    -   This solution supports separate bills. Alibaba Cloud provides the consolidated billing feature that allows resource groups to receive separate bills.
    -   This solution supports a shared bottom-layer network. Resource groups belong to the same Alibaba Cloud account and can share a VPC. The enterprise does not need to pay for peering connections. This helps reduce management costs.

## Solution

The resource group-based management solution can meet all requirements of the enterprise. This solution allows the enterprise to create three resource groups that correspond to the three projects by using one Alibaba Cloud account.

![Resource group-based solution](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2132559951/p14357.png)

1.  Create three RAM users: `Alice@secloud.onaliyun.com`, `Bob@secloud.onaliyun.com`, and `Charlie@secloud.onaliyun.com`.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

    **Note:** The following steps show how to specify a RAM user as a resource group administrator. The RAM user Alice is used as an example.

2.  Log on to the [Resource Management console](https://resourcemanager.console.aliyun.com/resource-groups).

3.  In the left-side navigation pane, click Resource Group. On the Resource Group tab, click **Create Resource Group**.

4.  In the Create Resource Group panel, specify **Resource Group Name** and **Display Name**, and click **OK**.

    **Note:** Create three resource groups: Game1, Game2, and Game3.

5.  Find a resource group that you created and click **Permission Management** in the **Actions** column.

6.  On the **Permissions** tab of the page that appears, click **Grant Permissions**.

7.  In the **Principal** field of the Grant Permission panel, enter `Alice@secloud.onaliyun.com`.

8.  In the Authorization Policy Name column of the Select Policy section, click `AdministratorAccess`.

9.  Click **OK**.

10. Click **Complete**.

    **Note:** Repeat the preceding steps to specify Bob and Charlie as resource group administrators.


Alice, Bob, and Charlie are the resource group administrators of Game1, Game2, and Game3. The administrators have the following permissions:

-   After an administrator logs on to the ECS console, the administrator can view the respective resource group. The administrator can also create and manage ECS instances.
-   After an administrator logs on to the Resource Management console, the administrator can add RAM users and grant resource access permissions to RAM users.

