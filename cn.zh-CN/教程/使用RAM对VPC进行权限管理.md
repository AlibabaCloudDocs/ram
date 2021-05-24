# 使用RAM对VPC进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对专有网络（VPC）进行权限管理，以满足RAM用户操作VPC的多种需求。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   使用RAM对VPC进行权限管理前，请先了解几个常用的权限策略：
    -   AliyunVPCFullAccess：为RAM用户授予VPC的完全管理权限。
    -   AliyunVPCReadOnlyAccess：为RAM用户授予VPC的只读访问权限。
-   使用RAM对VPC进行权限管理前，请先了解VPC的权限定义。详情请参见[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)。

## 将自定义权限策略授权给RAM用户

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  创建自定义权限策略。

    详细信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[VPC授权样例](#section_vgp_w4w_fwd)。

3.  在权限策略管理页面，找到目标权限策略，单击权限策略名称。

4.  单击**引用记录**页签，然后单击**新增授权**。

5.  在**被授权主体**区域，输入需要授权的RAM用户的名称或ID。

6.  单击**确定**。

7.  单击**完成**。

    **说明：** 您也可以直接对RAM用户或RAM用户组授予创建好的权限策略，详情信息，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)和[为用户组授权](/cn.zh-CN/用户组管理/为用户组授权.md)。


## VPC授权样例

-   示例1：对VPC的管理授权

    假设您的主账号ID为1234567，授权子账号管理该账号下的所有VPC，使某个RAM用户具有操作所有VPC的权限。

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

-   示例2：对VPC中VSwitch的管理授权

    假设您只想授权青岛地域下的VSwitch的管理权限，使某个RAM用户可以对青岛地域下的VSwitch进行创建、删除、绑定子网路由、解绑子网路由的操作，对于其它地域的VSwitch只有查看权限。

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

    假设您的主账号ID为11111111，在多个地域创建了VPC，该权限只授予某个RAM用户对杭州地域VPC的操作权限，且操作权限仅限于：允许新增、删除路由条目，允许创建子网路由并绑定VSwtich，对于其它地域的云产品只有查看权限。

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
    "acs:vpc:cn-hangzhou:11111111:*/*"
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


