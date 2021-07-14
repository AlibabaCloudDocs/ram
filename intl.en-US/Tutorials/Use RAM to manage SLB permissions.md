# Use RAM to manage SLB permissions

This topic describes how to manage Server Load Balancer \(SLB\) permissions of Resource Access Management \(RAM\) users. In the RAM console, you can create custom policies and attach the policies to the RAM users.

-   Before you manage the SLB permissions of RAM users, take note of the following system policies:

    -   AliyunSLBFullAccess: grants a RAM user the permissions to manage SLB instances.
    -   AliyunSLBReadOnlyAccess: grants read-only permissions on SLB instances.
    If the system policies cannot meet your business requirements, you can create custom policies.

-   Before you manage the SLB permissions of RAM users, take note of the SLB permissions. For more information, see [Authorize a RAM user](/intl.en-US/Classic Load Balancer/CLB Developer Guide/Developer Guide/Authorize a RAM user.md).

## Procedure

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Policy examples](#section_hwy_ypl_5gb).

3.  Attach the policy to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Policy examples

-   Example 1: Authorize a RAM user to manage two specific SLB instances.

    To authorize a RAM user to manage the SLB instances `i-001` and `i-002` in your Alibaba Cloud account, use the following sample script:

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:**

    -   The authorized RAM user can view all SLB instances, but can manage only the two specified SLB instances.
    -   The `Describe*` element is required in the policy. Otherwise, the authorized RAM user cannot view instances in the SLB console. However, the RAM user can call API operations or use the CLI or SDK to manage the two specified SLB instances.
-   Example 2: Authorize a RAM user to add an Elastic Compute Service \(ECS\) instance as a backend server of the SLB instance `slb-001`. The ID of the ECS instance is `i-001`.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        },
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:ecs:*:*:instance/i-001"]
        },
        {
           "Effect": "Allow",
           "Action": "slb:DescribeLoadBalancers",
           "Resource": "acs:slb:*:*:loadbalancer/*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** After you grant a RAM user permissions to manage an SLB instance based on the policy described in Example 1, you must also grant the following two permissions to the RAM user. Otherwise, the RAM user cannot add or remove ECS instances or configure the weights of ECS instances.

    -   Permissions on SLB instances
    -   Permissions on ECS instances
-   Example 3: Authorize a RAM user to perform ECS-related operations on a specific SLB instance.

    ```
    {
        "Statement": [{
                "Effect": "Allow",
                "Action": "slb:*",
                "Resource": [
                    "acs:slb:*:*:loadbalancer/i-001",
                    "acs:slb:*:*:loadbalancer/i-002"
                ]
            },
            {
                "Effect": "Allow",
                "Action": "slb:Describe*",
                "Resource": "*"
            },
            {
                "Effect": "Allow",
                "Action": "ecs:DescribeInstances",
                "Resource": "*"
            },
            {
                "Effect": "Allow",
                "Action": "slb:*",
                "Resource": [
                    "acs:ecs:*:*:instance/i-instance001",
                    "acs:ecs:*:*:instance/i-instance002"
                ]
            }
        ],
        "Version": "1"
    }
    ```

    **Note:** The preceding policy allows the RAM user to manage SLB instances `i-001` and `i-002`. Then, the RAM user can perform all ECS-related operations on the SLB instances. For example, the RAM user can add the ECS instances `i-instance001` and `i-instance002` as backend servers of the two specified SLB instances and configure the weights of the ECS instances. After this policy is attached to the RAM user, the RAM user can view the ECS instance list when the user selects ECS instances.


