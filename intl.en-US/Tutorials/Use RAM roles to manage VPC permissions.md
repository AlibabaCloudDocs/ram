# Use RAM roles to manage VPC permissions

This topic describes how to manage Virtual Private Cloud \(VPC\) permissions of a Resource Access Management \(RAM\) user. In the RAM console, you can create custom policies and attach them to the RAM user.

-   Before you manage the VPC permissions of RAM users, take note of the following system policies:

    -   AliyunVPCFullAccess: grants a RAM user the permissions to manage VPCs.
    -   AliyunECSReadOnlyAccess: grants read-only permissions on VPCs.
    If the system policies cannot meet your business requirements, you can create custom policies.

-   Before you manage the VPC permissions of RAM users, take note of the VPC permissions. For more information, see [RAM user authorization](/intl.en-US/API reference/RAM user authorization.md).

## Procedure

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Policy examples](#section_vgp_w4w_fwd).

3.  Attach the policy to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Policy examples

-   Example 1: Authorize a RAM user to manage all VPCs.

    To authorize a RAM user to manage all VPCs in your Alibaba Cloud account 1234567, use the following sample script:

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*"
                ],
                "Resource": [
                    "acs:vpc:*:1234567:*/*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```

-   Example 2: Authorize a RAM user to manage the vSwitches in a VPC.

    To authorize a RAM user to manage the vSwitches of the VPCs in the China \(Qingdao\) region, use the following policy. After the policy is attached to the RAM user, the RAM user can create, delete, associate, or disassociate subnet routes for the vSwitches of the VPCs in the China \(Qingdao\) region. The RAM user can only view the vSwitches in other regions.

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*",
                    "vpc:*VSwitch*",
                    "vpc:*RouteTable*"
                ],
                "Resource": [
                    "acs:vpc:cn-qingdao:*:*/*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```

-   Example 3: Authorize a RAM user to manage the route tables and routes in a specific region.

    To authorize a RAM user to manage all VPCs in the China \(Hangzhou\) region, use the following sample script. The RAM user belongs to your Alibaba Cloud account 1234567. After the RAM user is authorized, the RAM user can add or delete routes, create subnet routes, and associate vSwitches in this region. The RAM user can only view the cloud services in other regions.

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "slb:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "rds:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*",
                    "vpc:*RouteEntry*",
                    "vpc:*RouteTable*"
                ],
                "Resource": [                
    "acs:vpc:cn-hangzhou:1234567:*/*"
                ],
                "Condition": {}
            }
        ]
    }
    ```

-   Example 4: Authorize a RAM user to add or delete the routes in a specified route table.

    To authorize a RAM user to add or delete routes in a specific route table, use the following policy:

    ```
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*RouteEntry*"
                ],
                "Resource": [
                    "acs:vpc:cn-qingdao:*:routetable/vtb-m5e64ujkb7xn5zlq0xxxx"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```


