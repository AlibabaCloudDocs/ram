# 使用OneLogin进行角色SSO的示例

本文提供一个以OneLogin与阿里云进行角色SSO的示例，帮助您理解企业IdP与阿里云进行角色SSO的端到端配置流程。

本示例中，企业拥有一个阿里云账号、一个OneLogin管理员用户和多个OneLogin普通用户。您希望经过配置，使OneLogin普通用户直接使用OneLogin账号通过角色SSO的方式访问阿里云，而不是在阿里云重新创建账号。

关于什么是OneLogin，请参见[OneLogin帮助文档](https://onelogin.service-now.com/support?id=kb_article&sys_id=296c5c6bdb1c889024c780c74b9619f0&kb_category=60231113dbff4700d5505eea4b9619a9)。

## 步骤一：在OneLogin创建应用

1.  使用管理员用户登录[OneLogin](https://app.onelogin.com/login)。

2.  在账号头像的左侧，单击**Administration**，进入管理员页面。

3.  在顶部菜单栏，选择**Applications** \> **Applications**。

4.  在Applications页面的右上角，单击**Add App**。

5.  在Find Applications页面，搜索SAML Test Connector \(Advanced\)。

6.  在Add SAML Test Connector \(Advanced\)页面，配置应用程序的基本信息，然后单击**Save**。

    本示例中设置应用程序的**Display Name**为`LoginToAliyun`，其他参数保持默认值。

7.  在Info页面，鼠标悬浮在右上角的**More Actions**上，从下拉列表中单击**SAML Metadata**，下载身份提供商（IdP）元数据文件，并将其保存在本地计算机上。


## 步骤二：在阿里云创建身份提供商

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**角色SSO**页签，单击**创建身份提供商**。

4.  输入**身份提供商名称**（OneLogin）和**备注**。

5.  在**元数据文档**区域，单击**上传文件**，上传从[步骤一：在OneLogin创建应用](#section_78j_9js_fuc)获取的IdP元数据。

6.  单击**确定**。

    查看新创建的身份提供商详情，记录其ARN，方便您后续使用。


## 步骤三：在阿里云创建RAM角色

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**RAM角色管理**。

3.  单击**创建RAM角色**。

4.  选择可信实体类型为**身份提供商**，单击**下一步**。

5.  输入**角色名称**（例如：Reader-OneLogin）和**备注**。

6.  选择从[步骤二：在阿里云创建身份提供商](#section_7fz_jfo_srq)中创建的身份提供商（OneLogin）并查看限制条件后，单击**完成**。

7.  单击**关闭**。

    查看新创建的RAM角色详情，记录其ARN，方便您后续使用。


## 步骤四：在OneLogin配置应用

1.  使用管理员用户登录[OneLogin](https://app.onelogin.com/login)。

2.  创建自定义用户属性。

    1.  在顶部菜单栏，选择**Users** \> **Users**。

    2.  在Users页面，鼠标悬浮在右上角的**More Actions**上，从下拉列表中单击**Custom user fields**。

    3.  在Custom User Fields页面的右上角，单击**New User Field**。

    4.  在New User Field对话框，配置**Name**和**Shortname**，然后单击**Save**。

        本示例中，**Name**设置为`AliyunRoles for SSO`，**Shortname**设置为`AliyunRoles`。

3.  配置应用。

    1.  在顶部菜单栏，选择**Applications** \> **Applications**。

    2.  在Applications页面，单击[步骤一：在OneLogin创建应用](#section_78j_9js_fuc)创建的应用程序（LoginToAliyun）。

    3.  在左侧导航栏，单击**Configuration**。

    4.  在Configuration页面，配置以下信息，然后单击**Save**。

        -   **RelayState**：用来配置用户登录成功后跳转到的阿里云页面。

            **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为**RelayState**的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com，否则配置无效。若不配置，默认跳转到阿里云控制台首页。

        -   **Audience \(EntityID\)**：`urn:alibaba:cloudcomputing`。
        -   **Recipient**：`https://signin.aliyun.com/saml-role/sso`。
        -   **ACS \(Consumer\) URL**：`https://signin.aliyun.com/saml-role/sso`。
    5.  在左侧导航栏，单击**Parameters**。

    6.  在Parameters页面，单击![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6127069161/p269249.png)，添加第一条自定义应用属性。

        1.  在New Field对话框，设置**Field name**为`https://www.aliyun.com/SAML-Role/Attributes/Role`， 然后选中**Include in SAML assertion**和**Multi-value parameter**，最后单击**Save**。
        2.  在Edit Field https://www.aliyun.com/SAML-Role/Attributes/Role对话框，从**Default if no value selected**区域的两个下拉列表中分别选择**Aliyun Roles for SSO \(Custom\)**和**Semicolon Delimited input \(Multi-value output\)**，然后单击**Save**。
    7.  在Parameters页面，单击![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6127069161/p269249.png)，添加第二条自定义应用属性。

        1.  在New Field对话框，设置**Field name**为`https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`， 然后选中**Include in SAML assertion**，最后单击**Save**。
        2.  在Edit Field https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName对话框，从**Value**区域的下拉列表中选择**Email**，然后单击**Save**。

            **说明：** 您也可以根据实际需要设置**Value**为其他值，例如：**Username**、**userPrincipalName**等。

    8.  在Parameters页面的右上角，单击**Save**。


## 步骤五：在OneLogin创建用户并分配应用

1.  使用管理员用户登录[OneLogin](https://app.onelogin.com/login)。

2.  在顶部菜单栏，选择**Users** \> **Users**。

3.  创建用户。

    **说明：** 如果您已经拥有OneLogin用户，请跳过此步。

    1.  在Users页面的右上角，单击**New User**。

    2.  在New User页面，设置**First name**（例如：Jack）、**Last name**（例如：Lee）、**Username**（例如：jacklee）**Email**（例如：jacklee@example.com），然后单击**Save User**。

    3.  在User Info页面，鼠标悬浮在右上角的**More Actions**上，从下拉列表中单击**Change Password**，为用户设置登录密码，然后单击**Update**。

        为用户设置登录密码，以保证其可以正常登录到OneLogin。

4.  在User Info页面的**Custom Fields**区域，配置用户自定义属性**Aliyun Roles for SSO**的值。

    **Aliyun Roles for SSO**取值由RAM角色ARN和身份供应商ARN组成，两者之间用半角逗号（,）分隔，具体格式为`acs:ram::<account_id>:role/RoleName,acs:ram::<account_id>:saml-provider/ProviderName`。其中，RAM角色ARN从[步骤三：在阿里云创建RAM角色](#section_efr_wq8_8lw)获取，身份供应商ARN从[步骤二：在阿里云创建身份提供商](#section_7fz_jfo_srq)获取，<account\_id\>为阿里云账号ID。

    **说明：** 如果一个用户对应多个RAM角色，此处可配置多组值。每个RAM角色ARN和其对应的身份提供商ARN为一组值，多组值之间用半角分号（;）分隔。例如：`acs:ram::125022144354****:role/reader-onelogin,acs:ram::125022144354****:saml-provider/OneLogin;acs:ram::125022144354****:role/administrator-onelogin,acs:ram::125022144354****:saml-provider/OneLogin;acs:ram::158622887609****:role/finance,acs:ram::158622887609****:saml-provider/OneLogin2`。

5.  为用户分配应用。

    1.  在Applications页面，单击![添加](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6127069161/p269249.png)。

    2.  选择[步骤一：在OneLogin创建应用](#section_78j_9js_fuc)创建的应用（LoginToAliyun），然后单击**Continue**。

    3.  在弹出的对话框中，单击**Save**。

6.  在Users页面的右上角，单击右上角的**Save User**。

7.  重复步骤[4](#step_2gd_q5i_m44)~[6](#step_myy_gbe_bi7)，为其他OneLogin普通用户配置**Aliyun Roles for SSO**属性值并分配应用。


## 结果验证

1.  使用[步骤五：在OneLogin创建用户并分配应用](#section_t6y_awl_g5w)创建的用户（jacklee）登录[OneLogin](https://app.onelogin.com/login)。

2.  单击应用（LoginToAliyun）。

    如果成功跳转到您设置的**RelayState**对应页面（或默认的阿里云控制台首页），则说明登录成功。

    **说明：** 如果您在[步骤五：在OneLogin创建用户并分配应用](#section_t6y_awl_g5w)中为用户设置了多个角色，则需要先选择登录角色，才能访问阿里云。


