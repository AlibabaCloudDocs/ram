# Use RAM to manage ECS permissions

This topic describes how to manage ECS permissions of RAM users by creating policies in RAM.

-   An Alibaba Cloud account is created. If not, create one before proceeding. To create an Alibaba Cloud account, click [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   You have a basic understanding of the following common policies:
    -   AliyunECSFullAccess: grants a RAM user the permissions to manage ECS instances.
    -   AliyunECSReadOnlyAccess: grants a RAM user the read-only permission on ECS instances.
-   You have a basic understanding of ECS permissions. For more information, see [Authentication rules](/intl.en-US/API Reference/Authentication rules.md).

## Attach a custom policy to a RAM user

1.  Create a custom policy based on [ECS authorization examples](#section_01).

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md).

2.  On the **Policies** page, click the name of the policy.

3.  On the **References** tab, click **Grant Permission**.

4.  In the dialog box that appears, enter the name or ID of the RAM user in the **Principal** field. Then, select the RAM user from the auto-complete results.

5.  Click **OK**. Click **Finished**.

    **Note:** For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md) and [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md).


## ECS authorization examples

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
    -   The `Describe*` element is required in the policy. Otherwise, the authorized RAM user cannot view instances in the console. However, the RAM user can manage the two specified ECS instances by calling API operations or using the CLI or SDK.
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

    **Note:** You can grant ECS permissions to the RAM user by region and resource type. If you want to authorize a RAM user to view ECS instances in another region, you can replace `cn-qingdao` in `Resource` with the ID of the region. For a list of region IDs, see [Regions and zones]().

-   Example 3: Authorize a RAM user to create snapshots.

    If a RAM user cannot create disk snapshots after being granted the ECS instance administrator permission, you must grant disk permissions to the RAM user. In this example, the ECS instance ID is `inst-01` and the disk ID is `dist-01`.

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


