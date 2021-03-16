# RAM用户常见问题

本文介绍了RAM用户常见问题，包括登录、费用和权限等问题。

## RAM用户登录地址和登录方式是什么？

RAM用户登录地址如下： [RAM用户登录地址](https://signin.aliyun.com/)[RAM用户登录地址](https://signin-intl.aliyun.com/login.htm)。

**说明：** 通过登录[RAM控制台](https://ram.console.aliyun.com/)，在概览页可以快速查询登录RAM用户登录地址。当您使用此地址登录时，系统会为您自动填写默认域名，您只需补齐RAM用户名称即可。

通过登录[RAM控制台](https://partners-intl.console.aliyun.com/#/ram)，在概览页可以快速查询RAM用户登录地址。

**说明：** 当您使用此地址登录时，系统会为您自动填写默认域名，您只需补齐RAM用户名称即可。

RAM用户登录方式有以下几种：

-   方式一：`<$username>@<$AccountAlias>.onaliyun.com`。例如：`username@company-alias.onaliyun.com`。

    **说明：** RAM用户登录账号为UPN（User Principal Name）格式，即RAM控制台用户列表中所见的用户登录名称。<$username\>为RAM用户名称，<$AccountAlias\>.onaliyun.com为默认域名。

-   方式二：`<$username>@<$AccountAlias>`。例如：`username@company-alias`。

    **说明：** <$username\>为RAM用户名称，<$AccountAlias\>为账号别名。

-   方式三：如果创建了域别名，也可以使用域别名登录，格式为：`<$username>@<$DomainAlias>`。

    **说明：** <$username\>为RAM用户名称，<$DomainAlias\>为域别名。


## 什么是默认域名和域别名？

关于**默认域名**和**域别名**的概念，请参见[基本概念](/intl.zh-CN/产品简介/基本概念.md)。

查看并管理**默认域名**和**域别名**的操作步骤如下：

1.  使用阿里云账号或具有RAM管理权限的RAM用户登录[RAM控制台](https://ram.console.aliyun.com/)[RAM控制台](https://partners-intl.console.aliyun.com/#/ram)。
2.  在左侧导航栏的**人员管理**菜单下，单击**设置**。
3.  在**高级设置**页签下，可以查看并管理**默认域名**和**域别名**。

## RAM用户采购云产品需要什么权限？

-   如需采购按量付费的云产品，一般只需给RAM用户分配该产品的创建实例或创建资源的权限即可。
-   如需采购包年包月的云产品，还需要额外授予支付订单的权限，即授予用户`AliyunBSSOrderAccess`的权限策略。
-   有些产品在购买时需要连带使用或创建多种资源，这种情况下需要RAM用户具备相应资源的读取或创建权限。

    以下以创建ECS实例为例，说明具体需要的权限。

    如下权限策略表示RAM用户可以从实例启动模板创建ECS实例：

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:DescribeLaunchTemplates",
            "ecs:CreateInstance",
            "ecs:RunInstances",
            "ecs:DescribeInstances",
            "ecs:DescribeImages",
            "ecs:DescribeSecurityGroups"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "vpc:DescribeVpcs",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }
      ]
    }
    ```

    如果需要RAM用户在创建ECS实例过程中使用或创建其他资源，根据资源类型不同，还需要授予以下各类权限。

    **说明：**

    -   关于如何创建自定义策略，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)。
    -   关于如何为RAM用户授权，请参见[为RAM用户授权](/intl.zh-CN/用户管理/为RAM用户授权.md)。
    |操作|权限策略|
    |:-|:---|
    |使用快照创建ECS实例|`ecs:DescribeSnapshots`|
    |同时创建并使用新的VPC|    -   `vpc:CreateVpc`
    -   `vpc:CreateVSwitch` |
    |同时创建并使用新的安全组|    -   `ecs:CreateSecurityGroup`
    -   `ecs:AuthorizeSecurityGroup` |
    |指定实例角色|    -   `ecs:DescribeInstanceRamRole`
    -   `ram:ListRoles`
    -   `ram:PassRole` |
    |使用Keypair|    -   `ecs:CreateKeyPair`
    -   `ecs:DescribeKeyPairs` |
    |在专有宿主机上创建ECS实例|`ecs:AllocateDedicatedHosts`|


## 为什么RAM用户被授权后依然无访问权限？

-   请确认RAM用户的权限策略是否正确。
-   请检查RAM用户的自定义策略（个人权限策略、加入用户组的权限策略）是否对相关资源或操作设置了`"Effect": "Deny"`。

    例如：RAM用户拥有只读访问云服务器ECS的权限：`AliyunECSReadOnlyAccess`，但如果同时也拥有如下权限策略，根据RAM的Deny优先原则，该RAM用户不可以查看ECS资源。

    ```
    {
      "Statement": [
        {
          "Action": "ecs:*",
          "Effect": "Deny",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }              
    ```


## 为什么RAM用户没有权限仍然可以操作？

例如：RAM用户没有ECS的`AliyunECSFullAccess`或者`AliyunECSReadOnlyAccess`系统策略，也没有添加任何自定义策略，但可以查看实例列表。

-   请检查RAM用户所在的用户组权限策略中是否存在允许RAM用户操作的相应权限。
-   请确认当前已经被授权给RAM用户的其他权限策略中是否包含了相关权限。

    例如：云监控的系统权限策略为`AliyunCloudMonitorFullAccess`，此权限包括查看ECS实例列表的权限：`"ecs:DescribeInstances"`，查看RDS实例列表的权限：`"rds:DescribeDBInstances"`和查看SLB实例列表的权限`"slb:DescribeLoadBalancer"`等。当`AliyunCloudMonitorFullAccess`被授权给RAM用户后，该RAM用户便有权限查看ECS、RDS和SLB等产品的实例信息。


## 怎样授权RAM用户单独管理续费？

目前续费管理没有统一的权限策略，需要根据具体产品自定义权限策略。一般需要授权给RAM用户购买该产品所需要的权限以及支付订单的权限。

例如：RAM用户进行ECS的续费管理所需权限，请参见[RAM用户采购云产品需要什么权限](#section_ic3_fms_qfb)给RAM用户授权，同时需要授予`AliyunBSSOrderAccess`权限策略。

## RAM用户使用资源所产生的费用怎么计算？

-   RAM用户使用资源所产生的费用由其所属的阿里云账号承担。
-   RAM用户可以自动享有阿里云账号享有的折扣，无需特殊设置。
-   消费额度、信用额度和独立付款方式等财务相关属性均为阿里云账号内的全局设置，影响所有RAM用户。不支持为某个RAM用户单独设置。
-   RAM用户可以被授权进行充值操作，充值后的金额归属于阿里云账号。
-   RAM用户或RAM用户组不能作为独立的财务单元出账单。 若有阿里云账号内的分账需求，推荐您使用资源管理服务，详情请参见[资源组分账]()。

## 为什么RAM授权后，没有立刻在云产品中生效？

RAM采用多地域（Region）、多可用区（AZ）部署的高可用架构，数据在不同的Region间复制，并遵从最终一致性。当您在RAM中进行授权后，RAM会将授权信息同步分发到全球各个Region以及AZ中，为各个云产品提供鉴权能力。当某个AZ或者Region发生宕机后，RAM高可用容灾机制会切换到其它可用的AZ。

授权信息分发机制需要一定的时间来确保授权生效。当您进行授权变更后，需要等待一定的时间，授权才能在云产品中生效。

RAM会保证授权数据的最终一致性。

