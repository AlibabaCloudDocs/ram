# Use tags to grant access to ECS instances by group

This topic describes how to use tags to grant Resource Access Management \(RAM\) users access to Elastic Compute Service \(ECS\) instances by group. After authorization, RAM users can view and manage only the tagged resources.

In this example, you have 10 ECS instances. You want to authorize the developer team to manage 5 instances and the operator team to manage the other 5 instances. However, you want each team to view only the instances that you authorize each team to manage.

In this case, you can create two RAM user groups that are named developer and operator.

You can create two custom policies that are named policyForDevTeam and policyForOpsTeam.

You can create the following tags:

-   A tag that is attached to five ECS instances. The tag key is team and the tag value is dev.
-   A tag that is attached to the other five ECS instances. The tag key is team and the tag value is ops.

## Procedure

1.  Log on to the ECS console by using your Alibaba Cloud account. In the ECS console, create tags and attach the tags to your ECS instances.

    1.  Log on to the [ECS console](https://ecs.console.aliyun.com).

    2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

    3.  In the upper-left corner, select a region.

    4.  On the Instances page, find the specific instance, move the pointer over the ![Tag](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8508559951/p67422.png) icon in the **Tag** column, and then click **Edit Tags**.

    5.  In the Edit Tags dialog box, click **Create**.

    6.  Enter the tag key and tag value in the fields that appear and click **Confirm**.

    7.  Click **OK**.

    Repeat the preceding steps to attach the `team:dev` tag to five ECS instances and attach the `team:ops` tag to the other five ECS instances.

2.  Log on to the RAM console by using your Alibaba Cloud account and create two user groups that are named developer and operator.

    For more information, see [Create a user group](/intl.en-US/RAM User Group Management/Create a user group.md).

3.  Create RAM users and add each RAM user to the corresponding RAM user group.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md) and [Add a RAM user to a RAM user group](/intl.en-US/RAM User Group Management/Add a RAM user to a RAM user group.md).

4.  Create two custom policies that are named policyForDevTeam and policyForOpsTeam. Attach the policyForDevTeam policy to the developer group. Attach the policyForOpsTeam policy to the operator group.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Grant permissions to a RAM user group](/intl.en-US/RAM User Group Management/Grant permissions to a RAM user group.md).

    **Note:** After you attach a policy to a RAM user group, the RAM users in the group have the permissions that are included in the policy.

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
                    "ecs:tag/team": "ops"
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

    Each policy consists of two parts:

    -   The `"Action":"ecs:*"` part that includes `Condition` specifies the ECS instances to which the `team:dev` or `team:ops` tag is attached.
    -   The `"Action": "ecs:DescribeTag*"` part authorizes RAM users to query all tags in ECS. After a RAM user logs on to the ECS console, all existing tags are displayed. The RAM user must select the value of an authorized tag key to view the ECS instances to which the tag is attached.

## Verify the authorization

1.  Log on to the [ECS console](https://ecs.console.aliyun.com) as a RAM user.

2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.

3.  In the upper-left corner, select the region.

4.  On the Instances page, click **Tags** next to the search box.

5.  Move the pointer over a **tag key**. The list of tag values is displayed. Select a **tag value**. Then, only the ECS instances to which the tag is attached are displayed in the instance list.

    For example, a RAM user in the developer user group can view the list of ECS instances to which the `team:dev` tag is attached.


## References

You can use the procedure that is described in this topic to grant access to other ECS instances by group. The ECS resources include block storage devices, snapshots, images, security groups, elastic network interfaces \(ENIs\), dedicated hosts, and SSH key pairs.

