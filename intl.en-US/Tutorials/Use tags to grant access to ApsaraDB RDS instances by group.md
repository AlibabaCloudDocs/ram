# Use tags to grant access to ApsaraDB RDS instances by group

This topic describes how to use tags to grant Resource Access Management \(RAM\) users access to ApsaraDB RDS instances by group. After authorization, RAM users can view and manage only the tagged resources.

## Background information

In this example, you have 10 ApsaraDB RDS instances. You want to authorize the developer team to manage 5 instances and the operator team to manage the other 5. However, you want each team to view only the instances that you authorize each team to manage.

In this case, you can create a RAM user group named developer and another RAM user group named operator.

You can create a custom policy named policyForDevTeam and another custom policy named policyForOpsTeam.

You can create the following tags:

-   A tag that is attached to five ApsaraDB RDS instances. The tag key is team and the tag value is dev.
-   A tag that is attached to the other five ApsaraDB RDS instances. The tag key is team and the tag value is ops.

## Procedure

The procedure in which tags are used to grant access to ApsaraDB RDS instances by group is the same as the procedure in which tags are used to grant access to ECS instances by group. For more information, see [Use tags to grant access to ECS instances by group](/intl.en-US/Tutorials/Use tags to grant access to ECS instances by group.md).

You must create the following two custom policies to authorize the teams:

-   The policy policyForDevTeam for the RAM user group developer

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
            "StringEquals": {
              "rds:ResourceTag/team": "dev"
             }
           }
         },
        {
           "Action": "rds:DescribeTag*",
           "Effect": "Allow",
           "Resource": "*"
         }
      ],
      "Version": "1"
    }
    ```

-   The policy policyForOpsTeam for the RAM user group operator

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
            "StringEquals": {
              "rds:ResourceTag/team": "ops"
             }
           }
         },
        {
           "Action": "rds:DescribeTag*",
           "Effect": "Allow",
           "Resource": "*"
         }
      ],
      "Version": "1"
    }
    ```


Each policy consists of two parts:

-   The `"Action":"rds:*"` part that includes `Condition` specifies the ApsaraDB RDS instances to which the `team:dev` or `team:ops` tag is attached.
-   The `"Action": "rds:DescribeTag*"` part authorizes RAM users to query all tags in ApsaraDB RDS. After a RAM user logs on to the ApsaraDB RDS console, all existing tags are displayed. The RAM user must select the value of a tag key to view the ApsaraDB RDS instances to which the tag is attached.

## FAQ

If permission errors occur after you use tags to grant RAM users access to ApsaraDB RDS instances by group, check whether the following conditions are met:

-   The tag is attached to the ApsaraDB RDS instances.
-   The tag keys and values that are specified in the policies have the same keys and values as the tags that are attached to the ApsaraDB RDS instances.

    **Note:** The keys and values of tags in ApsaraDB RDS cannot contain uppercase letters. If you enter uppercase letters when you create a tag, ApsaraDB RDS converts the uppercase letters into lowercase letters.

-   The required policy is attached to the RAM users.
-   The region selected in the ApsaraDB RDS console is the region where the ApsaraDB RDS instances reside.
-   The corresponding tag value to filter the instances is selected.

**Note:** If a RAM user logs on to the ApsaraDB RDS console, the console returns the message "You do not have permission to perform this operation." Close the error message. This message appears because all ApsaraDB RDS instances are displayed by default. However, the RAM user is not authorized to view all ApsaraDB RDS resources.

