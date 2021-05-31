# 通过RAM对SLB进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对负载均衡（SLB）进行权限管理，以满足RAM用户操作SLB的多种需求。

-   使用RAM对SLB进行权限管理前，请先了解以下系统策略：

    -   AliyunSLBFullAccess：管理SLB的权限。
    -   AliyunSLBReadOnlyAccess：只读访问SLB的权限。
    当系统策略不能满足您的需求时，您可以创建自定义策略。

-   使用RAM对SLB进行权限管理前，请先了解SLB的权限定义。更多信息，请参见[RAM鉴权](/cn.zh-CN/传统型负载均衡CLB/CLB开发指南/API参考/RAM鉴权.md)。

## 操作步骤

1.  创建RAM用户。

    更多信息，请参见[创建RAM用户](/cn.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    更多信息，请参见[创建自定义策略](/cn.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)和[权限策略示例](#section_hwy_ypl_5gb)。

3.  为RAM用户授权。

    更多信息，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


## 权限策略示例

-   示例1：授权RAM用户管理两台指定的SLB实例。

    假设您的账号购买了多个实例，而作为RAM管理员，您希望仅授权其中的两个实例给某个RAM用户。实例ID分别为`i-001`、`i-002`。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:*",
          "Resource": [
                      "acs:slb:*:*:loadbalancer/i-001",
                      "acs:slb:*:*:loadbalancer/i-002"
                      ]
        },
        {
          "Effect": "Allow",
          "Action": "slb:Describe*",
          "Resource": "*"
        }
      ],
      "Version": "1"
    }
    ```

    **说明：**

    -   授予该权限策略的RAM用户可以查看所有的实例及资源，但只能管理其中两个实例。
    -   `Describe*`在权限策略中是必须的，否则用户在控制台将无法看到任何实例，但是使用API、CLI或SDK直接对两个实例进行管理是可以的。
-   示例2：将ECS实例加入负载均衡器`slb-001`。实例ID为`i-001`。

    ```
    {
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:slb:*:*:loadbalancer/slb-001"]
        },
        {
          "Effect": "Allow",
          "Action": "slb:AddBackendServers",
          "Resource": ["acs:ecs:*:*:instance/i-001"]
        },
        {
           "Effect": "Allow",
           "Action": "slb:DescribeLoadBalancers",
           "Resource": "acs:slb:*:*:loadbalancer/*"
        }
      ],
      "Version": "1"
    }
    ```

    **说明：** 即使RAM用户按照示例1被授予管理某个SLB实例的权限，但该RAM用户在SLB实例中添加或移除ECS服务器或设置权重时，仍然提示没有权限。原因是在负载均衡器中没有授予关于ECS服务器的两个权限：

    -   SLB的资源权限
    -   ECS服务器的权限
-   示例3：允许在特定SLB实例上执行任意ECS相关的操作。

    ```
    {
        "Statement": [{
                "Effect": "Allow",
                "Action": "slb:*",
                "Resource": [
                    "acs:slb:*:*:loadbalancer/i-001",
                    "acs:slb:*:*:loadbalancer/i-002"
                ]
            },
            {
                "Effect": "Allow",
                "Action": "slb:Describe*",
                "Resource": "*"
            },
            {
                "Effect": "Allow",
                "Action": "ecs:DescribeInstances",
                "Resource": "*"
            },
            {
                "Effect": "Allow",
                "Action": "slb:*",
                "Resource": [
                    "acs:ecs:*:*:instance/i-instance001",
                    "acs:ecs:*:*:instance/i-instance002"
                ]
            }
        ],
        "Version": "1"
    }
    ```

    **说明：** 上述权限策略表示：允许RAM用户在`i-001`和`i-002`这两个负载均衡器实例上执行所有管理操作，并允许在这两个实例上执行与ECS资源相关的所有操作。例如：将ECS实例`i-instance001`和`i-instance002`添加为这两个负载均衡实例的后端服务器或设置ECS服务器的权重等。使用此权限的过程中，RAM用户在选择ECS实例时可以看到所有实例的列表。


