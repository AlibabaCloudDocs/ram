# 利用标签对ECS实例进行分组授权

本文介绍了如何利用标签对ECS实例进行分组并授权，以满足RAM用户只能查看和操作被授权资源的需求。

假设您的账号购买了10个ECS实例，其中5个想要授权给developer团队，另外5个授权给operator团队。企业希望每个团队只能查看被授权的ECS实例，未被授权的不允许查看。

规划2个RAM用户组，名称命名为：developer、operator。

规划2个RAM自定义策略，名称命名为：policyForDevTeam、policyForOpsTeam。

规划2个标签，如下：

-   其中5个实例绑定一对标签，标签键是team，标签值是dev。
-   另外5个实例绑定另一对标签，标签键是team，标签值是ops。

## 操作步骤

1.  使用阿里云账号登录ECS控制台，为ECS实例创建并绑定标签。

    1.  登录[ECS控制台](https://ecs.console.aliyun.com)。

    2.  在左侧导航栏，选择**实例与镜像** \> **实例**。

    3.  在顶部菜单栏左上角处，选择地域。

    4.  在实例列表页面，将鼠标悬停目标实例**标签**列的![标签图标](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0608559951/p67422.png)图标上，然后单击**编辑标签**。

    5.  在编辑标签对话框，单击**新建标签**。

    6.  输入标签键和标签值，然后单击**确定**。

    7.  单击**确定**。

    按照上述步骤依次为5个ECS实例绑定标签`team:dev`，另外5个ECS实例绑定标签`team:ops`。

2.  使用阿里云账号登录RAM控制台，创建2个用户组：developer、operator。

    具体操作，请参见[创建用户组](/intl.zh-CN/用户组管理/创建用户组.md)。

3.  使用阿里云账号登录RAM控制台，创建不同的RAM用户，分别添加到2个用户组下。

    具体操作，请参见[创建RAM用户](/intl.zh-CN/用户管理/基本操作/创建RAM用户.md)、[为用户组添加RAM用户](/intl.zh-CN/用户组管理/为用户组添加RAM用户.md)。

4.  使用阿里云账号登录RAM控制台，创建2个自定义策略：policyForDevTeam和policyForOpsTeam，然后将自定义策略policyForDevTeam授权给用户组developer，将自定义策略policyForOpsTeam授权给用户组operator。

    具体操作，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)、[为用户组授权](/intl.zh-CN/用户组管理/为用户组授权.md)。

    **说明：** 授权后RAM用户将继承对应用户组的相关权限。

    policyForDevTeam策略内容如下：

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

    policyForOpsTeam策略内容如下：

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

    权限策略说明：

    -   带有`Condition`的`"Action": "ecs:*"`部分用于过滤标签为`team:dev`或`team:ops`的ECS实例。
    -   `"Action": "ecs:DescribeTag*"`用于展示所有ECS标签。当RAM用户在操作ECS控制台时，系统显示所有标签供RAM用户选择，只有当RAM用户选择了对应标签后，系统才能根据选中的标签过滤相应资源。

## 结果验证

1.  使用RAM用户登录[ECS控制台](https://ecs.console.aliyun.com)。

2.  在左侧导航栏，选择**实例与镜像** \> **实例**。

3.  在顶部菜单栏左上角处，选择地域。

4.  在实例列表页面，单击搜索栏旁边的**标签**。

5.  鼠标悬停在**标签键**上，选择对应的**标签值**，系统可以过滤出符合要求的ECS实例。

    例如：在用户组developer中的RAM用户，可以通过标签`team:dev`过滤，查看有权限访问的ECS实例。


## 更多信息

利用标签对块存储、快照、镜像、安全组、弹性网卡、专有宿主机、SSH密钥对等ECS资源进行分组授权的方法与上述对实例分组授权的方法相同。

