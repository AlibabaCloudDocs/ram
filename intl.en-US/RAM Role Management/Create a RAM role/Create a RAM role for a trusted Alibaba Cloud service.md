# Create a RAM role for a trusted Alibaba Cloud service

This topic describes how to create a Resource Access Management \(RAM\) role for a trusted Alibaba Cloud service. This type of RAM role is used to authorize access across Alibaba Cloud services.

Two types of RAM role are available for a trusted Alibaba Cloud service:

-   Normal service role: You must name the RAM role, select a trusted service, and then attach policies to the RAM role.
-   Service-linked role: You need only to select a trusted service. The name and policy of the RAM role are predefined by the service. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

## Create a normal service role

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role panel, select **Alibaba Cloud Service** for the Trusted entity type parameter and click **Next**.

5.  Select **Normal Service Role** for the Role Type parameter.

6.  Specify the **RAM Role Name** and **Note** parameters.

7.  Select a trusted service.

    **Note:** Available services are listed in the Select Trusted Service drop-down list.

8.  Click **OK**.


After you create a RAM role, the RAM role has no permissions. You can grant permissions to the RAM role. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).

## Create a service-linked role

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role panel, select **Alibaba Cloud Service** for the Trusted entity type parameter and click **Next**.

5.  Select **Service Linked Role** for the Role Type parameter.

6.  Select a service.

    After you select a service, you can view the name, description, and policy that are predefined for the service-linked role. You can click **View Policy Details** to view the detailed information of the policy.

    **Note:** Available services are listed in the Select Service drop-down list.

7.  Click **OK**.


**Related topics**  


[CreateRole](/intl.en-US/API Reference/API Reference (RAM)/Role management APIs/CreateRole.md)

[CreateServiceLinkedRole]()

