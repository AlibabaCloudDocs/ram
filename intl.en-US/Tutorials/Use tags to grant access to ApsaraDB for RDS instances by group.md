# Use tags to grant access to ApsaraDB for RDS instances by group

This topic describes how to use tags to grant Resource Access Management \(RAM\) users the access to ApsaraDB for RDS instances by group. After authorization, RAM users can view and manage only the tagged resources.

## Prerequisites

An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).

## Scenario

You have 10 ApsaraDB for RDS instances. You want to authorize the developer team to manage five instances and the operator team to manage the other five. However, you want each team to view and manage only the authorized instances.

## Procedure

For more information, see [Use tags to grant access to ECS instances by group](/intl.en-US/Tutorials/Use tags to grant access to ECS instances by group.md).

However, you must use a custom policy that includes the permissions on RDS instances. The following script is an example policy that you can use to authorize the developer team:

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

-   The statement that includes the `"Action": "rds:*"` condition grants RAM users the access to the RDS instances to which the `team:dev` tag is attached. The condition key in this statement is `rds:ResourceTag`.
-   The statement that includes the `"Action": "rds:DescribeTag*"` condition authorizes RAM users to view all RDS tags. After a RAM user logs on to the RDS console, all existing tags are displayed. The RAM user must select an authorized tag key and tag value to view the instances to which the selected tag is attached.

## FAQ

If permission errors occur after you use tags to grant RAM users the access to ApsaraDB for RDS instances by group, check the following items:

-   The tag is attached to the correct instances.
-   Tag keys and values specified in permission policies are the same as those attached to the instances.

    **Note:** Keys and values of RDS tags cannot contain uppercase letters. If you enter uppercase letters when you add a tag, RDS converts the uppercase letters into lowercase letters.

-   The required permission policy is attached to the RAM users.
-   The region selected in the console is the region to which the instances belong.
-   The corresponding tag value to filter the instances is selected.

**Note:** If a RAM user logs on to the RDS console, the console returns a message that "You do not have permission to perform this operation." Close the error message. This message appears because all RDS instances are displayed by default. However, the RAM user is not authorized to view all RDS resources.

