# FAQ about RAM users

This topic provides answers to some frequently asked questions \(FAQ\) about the logon, billing, and permissions of Resource Access Management \(RAM\) users.

## What are the logon URL and logon names of RAM users?

RAM users can use the following URL to log on: [Logon URL of RAM users](https://signin-intl.aliyun.com/login.htm).

**Note:** Alternatively, you can log on to the [RAM console](https://ram.console.aliyun.com/) by using an Alibaba Cloud account and find the logon URL of RAM users on the Overview page. If you use the URL on the Overview page to visit the logon page, the system automatically provides the default domain name so you need only to enter the username.

You can log on the console as a RAM user by using one of the following logon names:

-   Logon Name 1: `<$username>@<$AccountAlias>.onaliyun.com`. Example: `username@company-alias.onaliyun.com`.

    **Note:** The logon name of the RAM user is in the User Principal Name \(UPN\) format. All logon names that are listed in the RAM console follow this format. <$username\> indicates the username of the RAM user. <$AccountAlias\>.onaliyun.com indicates the default domain name.

-   Logon Name 2: `<$username>@<$AccountAlias>`. Example: `username@company-alias`.

    **Note:** <$username\> indicates the username of the RAM user. <$AccountAlias\> indicates the account alias.

-   Logon Name 3: `<$username>@<$DomainAlias>`. If you have configured a domain alias, you can use this logon name.

    **Note:** <$username\> indicates the username of the RAM user. <$DomainAlias\> indicates the domain alias.


## What are the default domain name and domain alias?

For more information about the **default domain name** and **domain alias**, see [Terms](/intl.en-US/Product Introduction/Terms.md).

To view and manage the **default domain name** and **domain alias**, perform the following steps:

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using an Alibaba Cloud account or as a RAM user who has the RAM management permissions.
2.  In the left-side navigation pane, choose **Identities** \> **Settings**.
3.  On the Settings page, click the **Advanced** tab. On the Advanced tab, you can view and manage the **default domain name** and **domain alias**.

## What permissions are required for a RAM user to purchase Alibaba Cloud services?

-   If a RAM user wants to purchase an Alibaba Cloud service on a pay-as-you-go basis, the permissions to create instances or resources are required.
-   If a RAM user wants to purchase an Alibaba Cloud service on a subscription basis, both the permissions to create instances and the permissions to make payments are required. To grant the permissions to make payments, you must attach the `AliyunBSSOrderAccess` policy to the RAM user.
-   If a RAM user purchases a service, the RAM user may need to use or create other resources. In this case, the permissions to read or create the resources are required.

    The following example is a policy that contains the permissions required to create Elastic Compute Service \(ECS\) instances.

    If the following policy is attached to a RAM user, the RAM user can create ECS instances from launch templates.

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:DescribeLaunchTemplates",
            "ecs:CreateInstance",
            "ecs:RunInstances",
            "ecs:DescribeInstances",
            "ecs:DescribeImages",
            "ecs:DescribeSecurityGroups"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "vpc:DescribeVpcs",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    If a RAM user wants to use or create other resources when the RAM user creates an ECS instance, the specific permissions are required. The following table lists the operations on other resources and the required policies.

    **Note:**

    -   For more information about how to create custom policies, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md).
    -   For more information about how to grant permissions to RAM users, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).
    |Operation|Policy|
    |:--------|:-----|
    |Use a snapshot to create an ECS instance|`ecs:DescribeSnapshots`|
    |Create and use a VPC|    -   `vpc:CreateVpc`
    -   `vpc:CreateVSwitch` |
    |Create and use a security group|    -   `ecs:CreateSecurityGroup`
    -   `ecs:AuthorizeSecurityGroup` |
    |Assign a RAM role to an ECS instance|    -   `ecs:DescribeInstanceRamRole`
    -   `ram:ListRoles`
    -   `ram:PassRole` |
    |Use an AccessKey pair|    -   `ecs:CreateKeyPair`
    -   `ecs:DescribeKeyPairs` |
    |Create an ECS instance on a dedicated host|`ecs:AllocateDedicatedHosts`|


## Why is a RAM user unable to access the resources after it has been granted the required permissions?

-   Check whether the policy that is attached to the RAM user is accurate.
-   Check whether custom policies that are attached to the RAM user contain `"Effect": "Deny"` to restrict the use of resources or operations. The policies may have been attached to the RAM user or a RAM user group that includes the RAM user.

    For example, both the `AliyunECSReadOnlyAccess` system policy and the following custom policy are attached to the RAM user. In this case, the RAM user is not allowed to view ECS resources because a Deny statement takes precedence over an Allow statement.

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Deny",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }              
    ```


## Why can a RAM user perform operations on resources without the required permissions?

For example, a RAM user can view the list of ECS instances even if the `AliyunECSFullAccess` system policy, the `AliyunECSReadOnlyAccess` system policy, or related custom policies are not attached to the RAM user.

-   Check whether the policies are attached to the RAM user group that includes the RAM user.
-   Check whether other polices attached to the RAM user contain the required permissions.

    For example, the `AliyunCloudMonitorFullAccess` system policy indicates full access to Cloud Monitor. This policy contains the following permissions: `"ecs:DescribeInstances"`, `"rds:DescribeDBInstances"`, and `"slb:DescribeLoadBalancer"`. If the `AliyunCloudMonitorFullAccess` policy is attached to the RAM user, the RAM user can view the information of ECS, ApsaraDB RDS, and Server Load Balancer \(SLB\) instances.


## How do I grant a RAM user the permissions to manage renewals?

You must create a custom policy to manage the renewals of a specific cloud service and attach the policy to the RAM user. A renewal management policy for all cloud services does not exist. The permissions to purchase a specific service and make payments are required for RAM users to manage renewals.

For example, if you want to authorize a RAM user to manage ECS instance renewals, you must grant the required permissions described in [What permissions are required for a RAM user to purchase Alibaba Cloud services?](#section_ic3_fms_qfb) You must also attach the `AliyunBSSOrderAccess` policy to the RAM user.

## How is a RAM user charged for consumed resources?

-   The fees that a RAM user is charged are billed to the parent Alibaba Cloud account.
-   By default, a RAM user can use the discounts that are applied to the parent Alibaba Cloud account.
-   Financial configurations such as the consumption budget, credit limit, and payment methods apply to all RAM users that belong to an Alibaba Cloud account. Financial configurations that apply to a single RAM user are unavailable.
-   RAM users can be authorized to add funds to the parent Alibaba Cloud account. The added funds belong to the Alibaba Cloud account.
-   RAM users and RAM user groups are not separately billed. If you want to obtain bills that contain detailed charges for each RAM user, we recommend that you use Resource Management. For more information, see [View billing statements by resource group]().

## I have granted permissions in RAM but the permissions do not immediately take effect on cloud services. Why?

RAM is deployed in multiple regions and zones to achieve high availability. RAM copies data between different regions and uses the eventual consistency model. After you grant permissions in RAM, RAM delivers the permission data to all Alibaba Cloud regions and zones. Then, all cloud services can use the information for authentication. If a failure occurs in a region or a zone, RAM switches over to an available region or zone based on its high-availability disaster recovery mechanism.

After RAM delivers the permission data, it takes a period for the permissions to take effect. Therefore, if you grant or change permissions, you must wait for a period before the permissions take effect on cloud services.

RAM ensures the eventual consistency of permission data.

