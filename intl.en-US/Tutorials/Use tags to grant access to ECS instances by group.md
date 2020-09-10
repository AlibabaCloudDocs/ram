# Use tags to grant access to ECS instances by group

This topic describes how to use tags to grant Resource Access Management \(RAM\) users the access to Elastic Compute Service \(ECS\) instances by group. After authorization, RAM users can view and manage only the tagged resources.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).

You have 10 ECS instances. You want to authorize the developer team to manage five instances and the operator team to manage the other five. However, you want each team to view and manage only the authorized instances.

You need to create two RAM user groups named developer and operator.

You need to create two RAM custom policies named policyForDevTeam and policyForOpsTeam.

You need to create the following tags:

-   A tag that is attached to five ECS instances. The tag key is team and the tag value is dev.
-   A tag that is attached to the other five ECS instances. The tag key is team and the tag value is ops.

## Procedure

1.  Log on to the ECS console with your Alibaba Cloud account. In the ECS console, create tags and attach the tags to your ECS instances.

    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

    2.  In the upper-left corner, select a region.

    3.  In the left-side navigation pane, choose **instances & Images** \> **Instances**. On the **Instances** page, find the ECS instance to which you want to attach a tag.

    4.  Move the pointer over the ![Tag](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8508559951/p67422.png) icon in the **Tag** column, and click **Edit Tags** in the tooltip that appears.

    5.  In the **Edit Tags** dialog box, click **Create**, enter the tag key and tag value in the fields that appear, and then click **Confirm**. If the tag has been created, click **Available Tags**, and select the tag key and the tag value from the drop-down list. After the tag is added, click **Confirm**.

    Perform the preceding steps to attach the `team:dev` tag to five ECS instances and attach the `team:ops` tag to the other five ECS instances.

2.  Log on to the RAM console with your Alibaba Cloud account and create two user groups named developer and operator.

    For more information, see [Create a RAM user group](/intl.en-US/RAM User Group Management/Create a RAM user group.md).

3.  Create RAM users and add each RAM user to the corresponding user group.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md) and [Add a RAM user to a RAM user group](/intl.en-US/RAM User Group Management/Add a RAM user to a RAM user group.md).

4.  Create two custom policies named policyForDevTeam and policyForOpsTeam. Attach the policyForDevTeam policy to the developer group and attach the policyForOpsTeam policy to the operator group.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md).

    **Note:** After you attach a policy to a user group, the RAM users in the group has the permissions that are included in the policy.

    The policyForDevTeam policy is defined by using the following script:

    ```
    {
        "Statement": [
        {
            "Action": "ecs:*",
            "Effect": "Allow",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ecs:tag/team": "dev"
                }
            }
        },
        {
            "Action": "ecs:DescribeTag*",
            "Effect": "Allow",
            "Resource": "*"
        }
        ],
        "Version": "1"
    }
    ```

    The policyForOpsTeam policy is defined by using the following script:

    ```
    {
        "Statement": [
        {
            "Action": "ecs:*",
            "Effect": "Allow",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "ecs:tag/team": "dev"
                }
            }
        },
        {
            "Action": "ecs:DescribeTag*",
            "Effect": "Allow",
            "Resource": "*"
        }
        ],
        "Version": "1"
    }
    ```

    Each policy consists of two statements:

    -   The statement that includes the `"Action": "ecs:*"` condition grants RAM users the access to the ECS instances to which the `team:dev` or `team:ops` tag is attached.
    -   The statement that includes `"Action": "ecs:DescribeTag*"` authorizes RAM users to view all ECS tags. After a RAM user logs on to the ECS console, all existing tags are displayed. The RAM user must select an authorized tag key and tag value to view the instances to which the selected tag is attached.

## Verify the authorization

1.  Log on to the [ECS console](https://ecs.console.aliyun.com) as a RAM user.

2.  In the upper-left corner, select the region.

3.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

4.  On the **Instances** page, click **Tags** next to the search box.

5.  Move the pointer over a tag key. The list of tag values is displayed. Select a tag value. Then, only the ECS instances to which the tag is attached are displayed in the instance list.

    For example, a RAM user in the developer user group can view the list of ECS instances to which the `team:dev` tag is attached.


## Related operations

You can use the procedure that is described in this topic to grant access to other ECS instances by group. The ECS resources include block storage devices, snapshots, images, security groups, elastic network interfaces \(ENIs\), dedicated hosts \(DDHs\), or Secure Shell \(SSH\) key pairs.

