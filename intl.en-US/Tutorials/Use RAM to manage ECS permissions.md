# Use RAM to manage ECS permissions

This topic describes how to manage Elastic Compute Service \(ECS\) permissions of Resource Access Management \(RAM\) users. In the RAM console, you can create custom policies and attach them to the RAM users.

-   Before you manage the ECS permissions of RAM users, take note of the following system policies:

    -   AliyunECSFullAccess: grants a RAM user the permissions to manage ECS instances.
    -   AliyunECSReadOnlyAccess: grants a RAM user the read-only permission on ECS instances.
    If the system policies cannot meet your business requirements, you can create custom policies.

-   Before you manage the ECS permissions of RAM users, take note of the ECS permissions. For more information, see [Authentication rules](/intl.en-US/API Reference/Authentication rules.md).

## Procedure

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Policy examples](#section_01).

3.  Attach the policy to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Policy examples

-   Example 1: Authorize a RAM user to manage two specified ECS instances.

    To authorize a RAM user to manage the ECS instances i-001 and i-002 in your Alibaba Cloud account, use the following sample script:

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": [
                      "acs:ecs:*:*:instance/i-001",
                      "acs:ecs:*:*:instance/i-002"
                      ]
        },
        {
          "Action": "ecs:Describe*",
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:**

    -   The authorized RAM user can view all ECS instances but can manage only the specified two ECS instances.
    -   The `Describe*` element is required in the policy. Otherwise, the authorized RAM user cannot view ECS instances in the ECS console. However, the RAM user can manage the two specified ECS instances by calling API operations or using the CLI or SDK.
-   Example 2: Authorize a RAM user to view ECS instances in the China \(Qingdao\) region, but do not allow the RAM user to view information about disks and snapshots.

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "ecs:Describe*",
          "Resource": "acs:ecs:cn-qingdao:*:instance/*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:** If you want to authorize a RAM user to view ECS instances in a different region, you can replace `cn-qingdao` in the `Resource` element with the ID of the region. For more information about region IDs, see [Regions and zones]().

-   Example 3: Authorize a RAM user to create snapshots.

    If a RAM user cannot create disk snapshots after the RAM user is granted administrator rights on the ECS instance, you must grant disk permissions to the RAM user. In this example, the ECS instance ID is `inst-01` and the disk ID is `dist-01`.

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Allow",
          "Resource": [
            "acs:ecs:*:*:instance/inst-01"
          ]
        },
        {
          "Action": "ecs:CreateSnapshot",
          "Effect": "Allow",
          "Resource": [
            "acs:ecs:*:*:disk/dist-01",
            "acs:ecs:*:*:snapshot/*"
          ]
        },
        {
          "Action": [
            "ecs:Describe*"
          ],
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```


