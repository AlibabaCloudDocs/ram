# Use RAM to manage ApsaraDB RDS permissions

This topic describes how to manage ApsaraDB RDS permissions of Resource Access Management \(RAM\) users. In the RAM console, you can create custom policies and attach them to the RAM users.

-   Before you manage the ApsaraDB RDS permissions of RAM users, take note of the following system policies:

    -   AliyunRDSFullAccess: grants a RAM user the permissions to manage ApsaraDB RDS instances.
    -   AliyunRDSReadOnlyAccess: grants read-only permissions on ApsaraDB RDS instances.
    If the system policies cannot meet your business requirements, you can create custom policies.

-   Before you manage the ApsaraDB RDS permissions of RAM users, take note of the ApsaraDB RDS permissions. For more information, see [Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md).

## Procedure

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Policy examples](#section_rhd_4ll_5gb).

3.  Attach the policy to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Policy examples

-   Example 1: Authorize a RAM user to manage two specified ApsaraDB RDS instances.

    To authorize a RAM user to manage the ApsaraDB RDS instances i-001 and i-002 in your Alibaba Cloud account, use the following sample script:

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": [
                      "acs:rds:*:*:dbinstance/i-001",
                      "acs:rds:*:*:dbinstance/i-002"
                      ]
        },
        {
          "Action": "rds:Describe*",
          "Effect": "Allow",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **Note:**

    -   The authorized RAM user can view all ApsaraDB RDS instances but can manage only the specified two ApsaraDB RDS instances.
    -   The `Describe*` element is required in the policy. Otherwise, the authorized RAM user cannot view instances in the ApsaraDB RDS console. However, the RAM user can manage the two specified ApsaraDB RDS instances by calling API operations or using the CLI or SDK.
-   Example 2: Authorize a RAM user to access Data Management \(DMS\).
    -   To authorize a RAM user to log on to a specific ApsaraDB RDS instance, use the following sample script:

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:dbinstance/rds783a0639ks5k7****"
            }
          ],
          "Version": "1"
        }
        ```

        **Note:** You must replace `rds783a0639ks5k7****` with the ID of the ApsaraDB RDS instance.

    -   To authorize a RAM user to log on to all ApsaraDB RDS instances, use the following sample script:

        ```
        {
          "Statement": [
            {
              "Action": "dms:LoginDatabase",
              "Effect": "Allow",
              "Resource": "acs:rds:*:*:*"
            }
          ],
          "Version": "1"
        }
        ```


