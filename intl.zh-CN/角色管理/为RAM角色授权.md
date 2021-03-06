# 为RAM角色授权

您可以为可信实体为阿里云账号、阿里云服务或身份提供商的RAM角色进行授权。本文为您介绍为RAM角色授权的几种方式。

**说明：** 服务关联角色的权限策略由关联的云服务定义，您不能为服务关联角色授权。服务关联角色的详情，请参见[服务关联角色](/intl.zh-CN/角色管理/服务关联角色.md)。

## 方式一：在RAM角色管理页面为RAM角色授权

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**RAM角色管理**。

3.  在RAM角色管理页面，单击目标RAM角色**操作**列的**添加权限**。

4.  在添加权限面板，为RAM角色添加权限。

    1.  选择授权应用范围。

        -   **整个阿里云账号**：权限在当前阿里云账号内生效。
        -   **指定资源组**：权限在指定的资源组内生效。

            **说明：** 指定资源组授权生效的前提是该云服务已支持资源组。更多信息，请参见[支持资源组的云服务]()。

    2.  输入被授权主体。

        被授权主体即需要授权的RAM角色，系统会自动填入当前的RAM角色，您也可以添加其他RAM角色。

    3.  选择权限策略。

        **说明：** 每次最多绑定5条策略，如需绑定更多策略，请分次操作。

5.  单击**确定**。

6.  单击**完成**。


## 方式二：在RAM角色管理页面为RAM角色精确授权

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**RAM角色管理**。

3.  在RAM角色管理页面，单击目标RAM角色**操作**列的**精确授权**。

4.  在添加权限面板，选择权限策略类型为**系统策略**或**自定义策略**，然后输入权限策略名称。

5.  单击**确定**。

6.  单击**关闭**。


## 方式三：在授权页面为RAM角色授权

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，选择**权限管理** \> **授权**。

3.  在授权页面，单击**新增授权**。

4.  在添加权限面板，为RAM角色添加权限。

    1.  选择授权应用范围。

        -   **整个阿里云账号**：权限在当前阿里云账号内生效。
        -   **指定资源组**：权限在指定的资源组内生效。

            **说明：** 指定资源组授权生效的前提是该云服务已支持资源组。更多信息，请参见[支持资源组的云服务]()。

    2.  输入被授权主体。

        被授权主体即需要授权的RAM角色。

    3.  选择权限策略。

        **说明：** 每次最多绑定5条策略，如需绑定更多策略，请分次操作。

5.  单击**确定**。

6.  单击**完成**。


**相关文档**  


[AttachPolicyToRole](/intl.zh-CN/API参考/API参考（RAM）/权限策略管理接口/AttachPolicyToRole.md)

