# 通过RAM对RDS进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对云数据库（RDS）进行权限管理，以满足RAM用户操作RDS的多种需求。

-   使用RAM对RDS进行权限管理前，请先了解以下系统策略：

    -   AliyunRDSFullAccess：管理RDS的权限。
    -   AliyunRDSReadOnlyAccess：只读访问RDS的权限。
    当系统策略不能满足您的需要时，您可以创建自定义策略。

-   使用RAM对RDS进行权限管理前，请先了解RDS的权限定义。更多信息，请参见[RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)。

## 操作步骤

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/cn.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_rhd_4ll_5gb)。

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：授权RAM用户管理2台指定的RDS实例。

    假设您的账号购买了多个实例，而作为RAM管理员，您希望仅授权其中的2个实例给某个RAM用户。实例ID分别为i-001、i-002。

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

    **说明：**

    -   授予该权限策略的RAM用户可以查看所有的实例及资源，但只能操作其中2个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，使用API、CLI或SDK直接对两个实例进行操作是可以的。
-   示例2：授权RAM用户访问DMS管理数据库内容。
    -   授权RAM用户登录指定RDS：

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

        **说明：** 请将`rds783a0639ks5k7****`替换为您要授权的RDS实例ID。

    -   授权RAM用户登录所有RDS：

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


