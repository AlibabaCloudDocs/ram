# 通过RAM对VPC进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对专有网络（VPC）进行权限管理，以满足RAM用户操作VPC的多种需求。

-   使用RAM对VPC进行权限管理前，请先了解以下系统策略：

    -   AliyunVPCFullAccess：管理VPC的权限。
    -   AliyunVPCReadOnlyAccess：只读访问VPC的权限。
    当系统策略不能满足您的需求时，您可以创建自定义策略。

-   使用RAM对VPC进行权限管理前，请先了解VPC的权限定义。更多信息，请参见[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)。

## 操作步骤

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/intl.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_vgp_w4w_fwd)。

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/intl.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：对VPC的管理授权

    假设您的阿里云账号ID为1234567，授权RAM用户管理该账号下的所有VPC，使某个RAM用户具有操作所有VPC的权限。

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

-   示例2：对VPC中vSwitch的管理授权

    假设您只想授权华北1（青岛）地域下的vSwitch的管理权限，使某个RAM用户可以对该地域下的vSwitch进行创建、删除、绑定子网路由、解绑子网路由的操作，对于其它地域的vSwitch只有查看权限。

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

-   示例3：只允许操作特定地域下的路由表以及路由表中的路由条目

    假设您的阿里云账号ID为1234567，在多个地域创建了VPC，该权限只授予某个RAM用户对华东1（杭州）地域VPC的操作权限，且操作权限仅限于：允许新增、删除路由条目，允许创建子网路由并绑定vSwitch，对于其它地域的云服务只有查看权限。

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

-   示例4：只允许修改特定路由表中的路由条目

    假设您只希望RAM用户新增、删除特定路由表中的路由条目。

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


