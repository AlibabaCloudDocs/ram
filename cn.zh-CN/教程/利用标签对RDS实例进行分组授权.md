# 利用标签对RDS实例进行分组授权

本文介绍了如何利用标签对RDS实例进行分组并授权，以满足RAM用户只能查看和操作被授权资源的需求。

## 背景信息

假设您的账号购买了10个RDS实例，其中5个想要授权给developer团队，另外5个授权给operator团队。企业希望每个团队只能查看被授权的实例，未被授权的不允许查看。

规划2个RAM用户组，名称命名为：developer、operator。

规划2个RAM自定义策略，名称命名为：policyForDevTeam、policyForOpsTeam。

规划2个标签，如下：

-   其中5个RDS实例绑定一对标签，标签键是team，标签值是dev。
-   另外5个RDS实例绑定另一对标签，标签键是team，标签值是ops。

## 利用标签对RDS分组授权的操作步骤

利用标签对RDS分组授权的操作步骤与对ECS实例分组授权的操作步骤部分相同，具体操作，请参见[利用标签对ECS实例进行分组授权](/cn.zh-CN/教程/利用标签对ECS实例进行分组授权.md)。

RDS相关自定义策略如下：

-   用户组developer的自定义策略policyForDevTeam

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

-   用户组operator的自定义策略policyForOpsTeam

    ```
    {
      "Statement": [
        {
          "Action": "rds:*",
          "Effect": "Allow",
          "Resource": "*",
          "Condition": {
            "StringEquals": {
              "rds:ResourceTag/team": "ops"
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


权限策略内容分为两部分：

-   带有`Condition`的`"Action": "rds:*"`部分用于过滤标签为`team:dev`或`team:ops`的RDS实例。
-   `"Action": "rds:DescribeTag*"`用于展示所有标签。当RAM用户在操作RDS控制台时，系统展示出所有标签供RAM用户选择，只有当RAM用户选择了标签值后，系统才能根据选中的标签值过滤相应资源。

## 常见问题

利用标签对RDS实例分组授权后，如果遇到RAM用户登录控制台报无权限的问题，请检查如下事项：

-   标签已被绑定到正确的实例上。
-   权限策略与实例上的标签键、标签值完全相同。

    **说明：** RDS的标签键值不可以使用大写字母，若输入大写字母在保存时会被自动转换成小写字母。

-   登录到RDS控制台的RAM用户已被授予了期望的权限策略。
-   控制台展示的当前地域是期望地域。
-   已选中相应标签值，此时系统才可以过滤出相应资源。

**说明：** RAM用户登录RDS控制台后，控制台会提示“您没有指定资源的操作权限，请先对资源进行授权操作。”，请关掉该错误提示。出现该错误提示的原因是控制台默认展示所有资源，而当前RAM用户并没有查看所有资源的权限，所以会报错。

