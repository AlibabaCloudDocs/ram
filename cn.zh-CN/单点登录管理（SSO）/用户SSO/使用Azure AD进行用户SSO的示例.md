# 使用Azure AD进行用户SSO的示例

本文提供一个以Azure AD（Azure Active Directory，以下简称 AAD）与阿里云进行用户SSO的示例，帮助您理解企业IdP与阿里云进行SSO的端到端配置流程。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   进行操作前，请确保您已经拥有AAD的账号。

## 在阿里云获取SAML服务提供商元数据

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**用户SSO**页签下，单击**SAML服务提供商元数据URL**后的**复制**按钮。

4.  在新的浏览器窗口中打开拷贝的链接，将XML文件另存到本地。

    **说明：** XML文件保存了阿里云作为一个SAML服务提供商的访问信息。您需要记录该文件中的`entityID`和`Location`的值，以便后续在AAD的配置中使用。


## 在AAD中创建应用

1.  以管理员身份登录[Azure门户](https://portal.azure.com/#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  单击**新建应用程序**。

    ![新建应用程序](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0599688951/p43721.png)

5.  在**添加应用程序**页面，单击**非库应用程序**。

    ![SSO_AAD_Application](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0599688951/p112044.png)

6.  在**添加自己的应用程序**页面，输入应用名称后，单击**添加**。

    **说明：** 本例中假设应用名称为AliyunSSODemo。

    ![SSO_AAD_Name](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1599688951/p112045.png)


## 在AAD中配置SAML

1.  单击AliyunSSODemo。

2.  在**概述**页面，单击**单一登录**。

    ![SSO_AAD_SAML](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1599688951/p112047.png)

3.  在选择单一登录方法页面下，单击**SAML**。

    ![SAML](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1599688951/p43727.png)

4.  在**设置SAML单一登录**页面进行配置。

    1.  在页面左上角，单击**上载元数据文件**，选择文件后，单击**添加**。

        ![上传元数据文件](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p43731.png)

        **说明：** 此处上传[在阿里云获取SAML服务提供商元数据](#section_1mf_pid_z9k)中获取的XML文件。

    2.  单击**基本SAML配置**区域右上角的![编辑](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p112341.png)图标。

    3.  在**基本SAML配置**对话框中，将上述XML文件中的`entityID`和`Location`分别作为**标识符（实体ID）**和**回复URL（断言使用者服务URL）**的值，并将**中继状态**设置为https://ram.console.aliyun.com，然后单击**保存**。

    4.  在**SAML签名证书**区域下的**联合元数据XML**，单击**下载**，将XML文件保存到本地。

        ![下载联合元数据XML](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p44054.png)


## 在阿里云创建RAM用户

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  创建RAM用户（username@\{id\}.onaliyun.com）。

    **说明：**

    -   请确保用户名前缀username与AAD中的用户名前缀保持一致。本例中假设username为u2。
    -   关于如何创建RAM用户，详情请参见[创建RAM用户](/cn.zh-CN/用户管理/创建RAM用户.md)。

## 在阿里云开启用户SSO

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  单击**用户SSO**。

4.  在**SSO登录设置**区域，单击**编辑**。

5.  在**SSO功能状态**区域，单击**开启**。

    **说明：** 用户SSO是一个全局功能，开启后，所有RAM用户都需要使用SSO登录。 如果您是通过RAM用户配置的，请先保留为关闭状态，您需要先完成RAM用户的创建，以免配置错误导致自己无法登录。您也可以通过主账号进行配置来规避此问题。

6.  单击**元数据文档**下的**上传文件**，上传从[在AAD中配置SAML](#section_755_ua6_j4m)中获取的XML文件。

7.  开启**辅助域名**开关并配置为u2.onmicrosoft.com。

8.  单击**确定**。


## 在AAD创建并分配用户

1.  以管理员身份登录[Azure门户](https://portal.azure.com/#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  在**名称**列表下，单击**AliyunSSODemo**。

5.  在左侧导航栏，单击**用户和组**。

6.  单击左上角的**添加用户**。

    ![添加用户](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p44178.png)

7.  单击**用户**，从用户列表中选择用户（u2），单击**选择**。

    ![选择用户](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1599688951/p44179.png)

8.  单击**分配**。


## 配置验证

1.  以管理员身份登录[Azure门户](https://portal.azure.com/#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  在**名称**列表下，单击**AliyunSSODemo**。

5.  在**概述**页面，单击**单一登录**。

6.  在**设置SAML单一登录**页面单击**Test**。

    ![test](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1599688951/p113621.png)

7.  在弹出的对话框中，单击**作为当前用户登录**。

    ![作为当前用户登录](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5726498951/p44191.png)


如果出现以下页面，表示配置成功。

![SSO_Okta配置验证](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0916498951/p111769.png)

