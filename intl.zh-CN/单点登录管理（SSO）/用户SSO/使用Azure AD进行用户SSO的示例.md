# 使用Azure AD进行用户SSO的示例

本文提供一个以Azure AD（Azure Active Directory，以下简称 AAD）与阿里云进行用户SSO的示例，帮助您理解企业IdP与阿里云进行SSO的端到端配置流程。

在本示例中，企业拥有一个阿里云账号和一个Azure AD租户。在Azure AD租户中，您有一个管理员用户（已授予全局管理员权限）和一个企业员工用户（u2）。您希望经过配置，使企业员工用户（u2）可以通过RAM用户身份直接访问阿里云。

您需要通过管理员用户（已授予全局管理员权限）执行本示例AAD中的操作。关于如何在AAD中创建用户和为用户授权，请参见[AAD文档](https://docs.microsoft.com/zh-cn/azure/active-directory/fundamentals)。

## 步骤1：在阿里云获取SAML服务提供商元数据

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**用户SSO**页签下，单击**SAML服务提供商元数据URL**后的**复制**。

4.  在新的浏览器窗口中打开拷贝的链接，将XML文件另存到本地。

    **说明：** XML文件保存了阿里云作为一个SAML服务提供商的访问信息。您需要记录该文件中的`entityID`和`Location`的值，以便后续在AAD的配置中使用。


## 步骤2：在AAD中创建应用

1.  管理员用户登录[Azure门户](https://portal.azure.com/?l=en.en-us#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，选择**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  单击**新建应用程序**。

5.  在**浏览Azure AD库（预览）**页面，单击**创建你自己的应用程序**。

6.  在**创建你自己的应用程序**页面，输入应用名称（例如：AliyunSSODemo），并选择**集成库中未发现的任何其他应用程序**，然后单击**创建**。


## 步骤3：在AAD中配置SAML

1.  在**AliyunSSODemo**页面，单击左侧导航栏的**单一登录**。

2.  在选择单一登录方法页面下，单击**SAML**。

3.  在**设置SAML单一登录**页面进行以下配置。

    1.  在页面左上角，单击**上载元数据文件**，选择文件后，单击**添加**。

        ![上载元数据文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4289407061/p187566.png)

        **说明：** 此处上传[步骤1：在阿里云获取SAML服务提供商元数据](#section_1mf_pid_z9k)中获取的XML文件。

    2.  在**基本SAML配置**页面，配置以下信息，然后单击**保存**。

        -   **标识符（实体 ID）**：从上一步的元数据文件中自动读取`entityID`的值。
        -   **回复 URL（断言使用者服务 URL）**：从上一步的元数据文件中自动读取`Location`的值。
        -   **中继状态**：用来配置用户SSO登录成功后跳转到的阿里云页面。

            **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为**中继状态**的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com，否则配置无效。若不配置，默认跳转到阿里云控制台首页。

    3.  在**SAML签名证书**区域，执行以下操作，获取**联合元数据XML**。

        1.  单击**添加证书**。
        2.  添加新证书并单击**保存**。
        3.  刷新当前页面，单击**下载**，获取**联合元数据XML**。

            ![下载联合元数据XML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0929896061/p44054.png)


## 步骤4：在AAD分配用户

1.  管理员用户登录[Azure门户](https://portal.azure.com/?l=en.en-us#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，选择**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  在**名称**列表下，单击**AliyunSSODemo**。

5.  在左侧导航栏，单击**用户和组**。

6.  单击左上角的**添加用户**。

    ![添加用户](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p44178.png)

7.  单击**用户**，从用户列表中选择用户（u2），单击**选择**。

    ![选择用户](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1599688951/p44179.png)

8.  单击**分配**。


## 步骤5：在阿里云创建RAM用户

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  创建RAM用户（<username\>@<AccountAlias\>.onaliyun.com）。

    **说明：**

    -   <username\>为RAM用户名称，<AccountAlias\>.onaliyun.com为默认域名。请确保<username\>与AAD中的用户名前缀保持一致。本示例中<username\>为u2。
    -   关于如何创建RAM用户，详情请参见[创建RAM用户](/intl.zh-CN/用户管理/创建RAM用户.md)。

## 步骤6：在阿里云开启用户SSO

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  单击**用户SSO**。

4.  在**SSO登录设置**区域，单击**编辑**。

5.  在**SSO功能状态**区域，单击**开启**。

    **说明：** 用户SSO是一个全局功能，开启后，所有RAM用户都需要使用SSO登录。如果您是通过RAM用户配置的，请先保留为关闭状态，您需要先完成RAM用户的创建，以免配置错误导致自己无法登录。您也可以通过阿里云账号进行配置来规避此问题。

6.  单击**元数据文档**下的**上传文件**，上传从[步骤3：在AAD中配置SAML](#section_755_ua6_j4m)中获取的XML文件。

7.  开启**辅助域名**开关，并配置为AAD中的用户名Email后缀。

    例如：本示例中AAD用户（u2）的完整用户名为u2@test.onmicrosoft.com，则此处填写test.onmicrosoft.com。

8.  单击**确定**。


## 配置验证

-   从阿里云侧发起登录
    1.  在[RAM控制台](https://ram.console.aliyun.com/)的**概览**页，复制RAM用户的登录地址。
    2.  将鼠标悬停在右上角头像的位置，单击**退出登录**或使用新的浏览器打开复制的RAM登录地址。
    3.  单击**使用企业账号登录**，系统会自动跳转到AAD的登录页面。

        ![企业账户登录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3388646061/p185807.png)

    4.  使用用户（u2）登录。

        系统将自动单点登录并重定向到您指定的**中继状态**页面。如果未指定**中继状态**或超出允许范围，则系统会访问如下阿里云控制台首页。

        ![用户SSO配置验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5289407061/p111769.png)

-   从AAD侧发起登录
    1.  获取用户访问URL
        1.  管理员用户登录[Azure门户](https://portal.azure.com/?l=en.en-us#home)。
        2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。
        3.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。
        4.  单击应用程序**AliyunSSODemo**。
        5.  在左侧导航栏，单击**属性**，获取**用户访问URL**。

            **用户访问URL**是用户直接从其浏览器访问此应用程序的链接。

            ![用户访问URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5289407061/p187940.png)

    2.  用户（u2）从管理员用户处获取上述**用户访问URL**在浏览器中输入该URL，使用自己的账号登录。

        系统将自动单点登录并重定向到您指定的**中继状态**页面。如果未指定**中继状态**或超出允许范围，则系统会访问如下阿里云控制台首页。

        ![用户SSO配置验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5289407061/p111769.png)


