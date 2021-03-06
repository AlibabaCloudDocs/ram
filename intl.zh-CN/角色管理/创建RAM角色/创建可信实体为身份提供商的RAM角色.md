# 创建可信实体为身份提供商的RAM角色

本文介绍如何创建可信实体为身份提供商的RAM角色。该RAM角色主要用于实现与阿里云的角色SSO。

请确保您已创建了身份提供商。具体操作，请参见[创建身份提供商](/intl.zh-CN/单点登录管理（SSO）/角色SSO/身份提供商/创建身份提供商.md)。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**RAM角色管理**。

3.  在RAM角色管理页面，单击**创建RAM角色**。

4.  在创建RAM角色面板，选择可信实体类型为**身份提供商**，然后单击**下一步**。

5.  输入**角色名称**和**备注**。

6.  选择身份提供商并查看限制条件，然后单击**完成**。

    **说明：** 目前只支持一个条件关键字`saml:recipient`，必选且不能修改。


成功创建RAM角色后，该RAM角色没有任何权限，您可以为该RAM角色授权。具体操作，请参见[为RAM角色授权](/intl.zh-CN/角色管理/为RAM角色授权.md)。

**相关文档**  


[CreateRole](/intl.zh-CN/API参考/API参考（RAM）/角色管理接口/CreateRole.md)

