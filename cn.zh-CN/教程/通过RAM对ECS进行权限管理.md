# 通过RAM对ECS进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对云服务器（ECS）进行权限管理，以满足RAM用户操作ECS的多种需求。

-   使用RAM对ECS进行权限管理前，请先了解以下系统策略：

    -   AliyunECSFullAccess：管理ECS的权限。
    -   AliyunECSReadOnlyAccess：只读访问ECS的权限。
    当系统策略不能满足您的需要时，您可以创建自定义策略。

-   使用RAM对ECS进行权限管理前，请先了解ECS的权限定义。更多信息，请参见[鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)。

## 操作步骤

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/cn.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_01)。

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：授权RAM用户管理2台指定的ECS实例。

    假设您的账号购买了多个实例，而作为RAM管理员，您希望仅授权其中的2个实例给某个RAM用户。实例ID分别为i-001、i-002。

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

    **说明：**

    -   授予该权限策略的RAM用户可以查看所有的实例及资源，但只能操作其中2个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，但使用API、CLI或SDK直接对两个实例进行操作是可以的。
-   示例2：授权RAM用户仅可以查看华北1（青岛）地域的ECS实例，但不允许查看磁盘及快照信息。

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

    **说明：** 如果您想授权RAM用户查看其他地区的ECS实例，可以将`Resource`中的`cn-qingdao`替换为其他地域ID。关于地域ID，请参见[地域和可用区]()。

-   示例3：授权RAM用户创建快照。

    如果RAM用户已拥有ECS实例管理员权限， 但仍不能创建磁盘快照，再次授予RAM用户指定磁盘的权限即可正常使用。ECS实例ID为`inst-01`，磁盘ID为`dist-01`。

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


