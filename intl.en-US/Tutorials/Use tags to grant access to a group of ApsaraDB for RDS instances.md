# Use tags to grant access to a group of ApsaraDB for RDS instances

This topic describes how to use tags to grant Resource Access Management \(RAM\) users access to a group of ApsaraDB for RDS instances. After authorization, RAM users can view and manage only the tagged resources.

## Prerequisites

An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).

## Scenario

Assume that you have 10 ApsaraDB for RDS instances. You want to authorize the developer team to manage five instances and the operator team to manage the other five. However, you want each team to view and manage only the authorized instances.

## Procedure

The procedure for using tags to grant access to ApsaraDB for RDS instances by group is the same as that for using tags to grant access to ECS instances by group. For more information, see [Use tags to grant access to a group of ECS instances](/intl.en-US/Tutorials/Use tags to grant access to a group of ECS instances.md).

However, you must use a custom policy that includes the permissions on ApsaraDB for RDS instances. The following script is an example policy that you can use to authorize the developer team:

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

The policy consists of two statements:

-   The statement that includes the `"Action": "rds:*"` `condition` grants RAM users access to the ApsaraDB for RDS instances to which the `team:dev` tag is attached. The `Condition` key in this statement is `rds:ResourceTag`.
-   The statement that includes the `"Action": "rds:DescribeTag*"` condition authorizes RAM users to view all tags. After a RAM user logs on to the ApsaraDB for RDS console, all existing tags are displayed. The RAM user must select the value of an authorized tag key to view the instances to which the tag is attached.

## FAQ

If permission errors occur after you use tags to grant RAM users access to a group of ApsaraDB for RDS instances, check whether the following conditions are met:

-   The tag is attached to the instances.
-   The tag keys and values that are specified in the policies have the same keys and values as the tags that are attached to the instances.

    **Note:** The keys and values of tags in ApsaraDB for RDS cannot contain uppercase letters. If you enter uppercase letters when you add a tag, ApsaraDB for RDS converts the uppercase letters into lowercase letters.

-   The required policy is attached to the RAM users that are logged on.
-   The region selected in the ApsaraDB for RDS console is the region to which the instances belong.
-   The corresponding tag value to filter the instances is selected.

**Note:** If a RAM user logs on to the ApsaraDB for RDS console, the console returns the message "You do not have permission to perform this operation." Close the error message. This message appears because all ApsaraDB for RDS instances are displayed by default. However, the RAM user is not authorized to view all ApsaraDB for RDS resources.

