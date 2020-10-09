# 使用Okta进行用户SSO的示例

本文提供一个以Okta与阿里云进行用户SSO的示例，帮助您理解企业IdP与阿里云进行SSO的端到端配置流程。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.aliyun.com/register/register.htm)。
-   进行操作前，请确保您已经拥有Okta账号。

    **说明：** 如果仅作为测试用途，您可以在Okta官网申请有效期为30天的账号。


## 步骤1：在阿里云获取SAML服务提供商元数据

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**用户SSO**页签下，单击**SAML服务提供商元数据URL**后的**复制**按钮。

4.  在新的浏览器窗口中打开复制的链接，将XML文件另存到本地。

    **说明：** XML文件保存了阿里云作为一个SAML服务提供商的访问信息。您需要记录XML文件中`EntityDescriptor`元素的`entityID`属性值和`AssertionConsumerService`元素的`Location`属性值，以便后续在Okta的配置中使用。


## 步骤2：在Okta创建支持SAML SSO的应用

1.  登录[Okta门户](https://www.okta.com/)。

    **说明：** 您需要提前在手机端下载Okta Verify应用，登录时需要输入6位动态验证码。

2.  将鼠标悬停在页面右上方的账号图标上，单击**Your Org**。

3.  单击**Admin**。

    ![SSO_Okta_管理员](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6790549951/p111967.png)

4.  在Okta顶部菜单栏，单击**Applications**。

    ![SSO_Okta_Applications](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6790549951/p111964.png)

5.  单击**Add Application**。

6.  单击**Create New App**。

7.  **Platform**选择为**Web**，**Sign on method**选择为**SAML 2.0**，单击**Create**。

8.  配置应用名称为AliyunSSODemo，单击**Next**。

9.  配置SAML，然后单击**Next**。

    ![SAML配置](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/1111322061/p139864.png)

    -   **Single sign on URL**为[步骤1：在阿里云获取SAML服务提供商元数据](#section_7q5_glq_tbn)中记录的`Location`。
    -   **Audience URI**为[步骤1：在阿里云获取SAML服务提供商元数据](#section_7q5_glq_tbn)中记录的`entityID`。
    -   **Default RelayState**用来配置用户登录成功后跳转到的阿里云页面。

        **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为**Default RelayState**的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com，否则配置无效。若不配置，默认跳转到阿里云控制台首页。

    -   **Name ID format**选择**Persistent**。
    -   **Application username**选择**Email**。
10. 根据需要选择合适的应用类型，然后单击**Finish**。


## 步骤3：在Okta获取SAML IdP元数据

1.  在Okta顶部菜单栏，单击**Applications**。

2.  单击目标应用名称（AliyunSSODemo）。

3.  在**Sign On**页签下，单击**Identity Provider metadata**，将IdP元数据另存到本地。

    ![SSO_Okta_Sign On](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p111987.png)


## 步骤4：在阿里云开启用户SSO

1.  在RAM控制台的左侧导航栏，单击**SSO管理**。

2.  单击**用户SSO**。

3.  在**SSO登录设置**区域，单击**编辑**。

4.  在**SSO功能状态**区域，单击**开启**。

    **说明：** 用户SSO是一个全局功能，开启后，所有RAM用户都需要使用SSO登录。 如果您是通过RAM用户配置的，请先保留为关闭状态，您需要先完成RAM用户的创建，以免配置错误导致自己无法登录。您也可以通过主账号进行配置来规避此问题。

5.  单击**元数据文档**下的**上传文件**，上传从[步骤3：在Okta获取SAML IdP元数据](#section_gja_2u2_so7)中获取的IdP元数据。

6.  开启**辅助域名**开关并配置为Okta中的用户名Email后缀。

    **说明：** 如果您的Okta中存在多种Email后缀的用户，则只有以此处配置的后缀结尾的Email地址可以登录到阿里云。

7.  单击**确定**。


## 步骤5：在Okta创建用户并分配应用

1.  在Okta顶部菜单栏，单击**Directory** \> **People**。

    ![OSS_Okta_poeple](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p113589.png)

2.  单击**Add Person**，在**Add Person**页面，填写基本信息并将**Primary email**配置为test@example.com。

3.  在**Password**区域，勾选**Send user activation email now**，单击**Save**。

    **说明：** 根据页面提示激活Okta用户。

4.  返回Okta顶部菜单栏，单击**Applications**。

5.  单击目标应用名称（AliyunSSODemo）后，在**Assignments**页签下，单击**Assign** \> **Assign to People**。

6.  单击目标用户（test@example.com）后的**Assign**。

7.  单击**Save and Go Back**。

8.  单击**Done**。


## 步骤6：在阿里云创建RAM用户

1.  在RAM控制台的左侧导航栏，单击**人员管理** \> **用户**。

2.  单击**创建用户**。

3.  输入**登录名称**和**显示名称**。

    **说明：** 请确保RAM用户的登录名称前缀与Okta中的用户名前缀保持一致，本示例中为test。

4.  在**访问方式**区域下，选择**控制台访问**，并设置登录密码等参数。

5.  单击**确定**。


## 配置验证

-   从阿里云侧发起登录

    1.  在[RAM控制台](https://ram.console.aliyun.com/)的**概览**页，复制RAM用户的登录地址。
    2.  将鼠标悬停在右上角头像的位置，单击**退出登录**或使用新的浏览器打开复制的RAM登录链接。
    3.  单击**使用企业账户登录**，系统会自动跳转到Okta的登录页面。
    4.  在Okta的登录界面，输入用户名（test@example.com）和密码，单击**登录**。
    系统将自动单点登录并重定向到您指定的**DefaultRelayState**页面。如果未指定**DefaultRelayState**或超出允许范围，则系统会访问如下阿里云控制台首页。如果出现以下页面，表示配置成功。

    ![SSO_Okta配置验证](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0916498951/p111769.png)

-   从Okta侧发起登录

    使用Okta用户登录[Okta门户](https://www.okta.com/)，在Okta的主页，找到并单击**AliyunSSODemo**应用。

    系统将自动单点登录并重定向到您指定的**DefaultRelayState**页面。如果未指定**DefaultRelayState**或超出允许范围，则系统会访问如下阿里云控制台首页。如果出现以下页面，表示配置成功。

    ![SSO_Okta配置验证](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0916498951/p111769.png)


