# 使用Azure AD进行角色SSO的示例

本文提供一个以Azure AD（Azure Active Directory，以下简称 AAD）与阿里云进行角色SSO的示例，帮助用户理解企业IdP与阿里云进行SSO的端到端配置流程。

在本示例中，企业拥有一个阿里云账号（Account1）和一个Azure AD租户。在Azure AD租户中，您有一个管理员用户（已授予全局管理员权限）和一个企业员工用户（u2）。您希望经过配置，使得企业员工用户（u2）在登录Azure AD后，通过角色SSO访问阿里云账号（Account1）。

您需要通过管理员用户（已授予全局管理员权限）执行本示例AAD中的操作。关于如何在AAD中创建用户和为用户授权，请参见[AAD文档](https://docs.microsoft.com/zh-cn/azure/active-directory/fundamentals)。

![场景](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4726498951/p44059.png)

## 步骤1：在AAD库中添加应用程序

1.  管理员用户登录[Azure门户](https://portal.azure.com/?l=en.en-us#home)。

2.  单击主页的![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p112037.png)图标。

3.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

4.  单击**新建应用程序**。

5.  搜索**Alibaba Cloud Service \(Role-based SSO\)**并单击选择。

6.  输入应用名称，然后单击**创建**。

    本示例中，使用默认应用名称**Alibaba Cloud Service \(Role-based SSO\)**，您也可以自定义应用名称。

7.  在Alibaba Cloud Service \(Role-based SSO\)页面，单击左侧导航栏的**属性**，复制并保存**对象ID**。


## 步骤2：配置AAD SSO

1.  在Alibaba Cloud Service \(Role-based SSO\)页面，单击左侧导航栏的**单一登录**。

2.  在选择单一登录方法页面，单击**SAML**。

3.  在设置SAML单一登录页面进行配置。

    1.  在页面左上角，单击**上传元数据文件**，选择文件后，单击**添加**。

        ![上传元数据文件](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p43731.png)

        **说明：** 您可以通过以下URL获取元数据文件： `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。

    2.  在**基本SAML配置**页面，配置以下信息，然后单击**保存**。

        -   **标识符（实体 ID）**：从上一步的元数据文件中自动读取`entityID`的值。
        -   **回复 URL（断言使用者服务 URL）**：从上一步的元数据文件中自动读取`Location`的值。
        -   **中继状态**：用来配置角色SSO登录成功后跳转到的阿里云页面。

            **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为**中继状态**的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com，否则配置无效。若不配置，默认跳转到阿里云控制台首页。

    3.  在**用户属性和声明**区域，单击![编辑](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p112341.png)图标。

    4.  单击**添加新的声明**，配置以下信息，然后单击**保存**。

        -   在**名称**区域，输入`Role`。
        -   在**命名空间**区域，输入`https://www.aliyun.com/SAML-Role/Attributes`。
        -   在**源**区域，选择**属性**。
        -   在**源属性**区域，从下拉列表中选择`user.assignedroles`。
    5.  重复上述步骤，添加一个新的声明。

        -   在**名称**区域，输入`RoleSessionName`。
        -   在**命名空间**区域，输入`https://www.aliyun.com/SAML-Role/Attributes`。
        -   在**源**区域，选择**属性**。
        -   在**源属性**区域，从下拉列表中选择`user.userprincipalname`。
    6.  在**SAML签名证书**区域，单击**下载**，获取**联合元数据XML**。

        ![下载联合元数据XML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0929896061/p44054.png)


## 步骤3：在阿里云创建身份提供商

1.  阿里云账号（Account1）登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**角色SSO**页签下，单击**创建身份提供商**。

4.  输入**身份提供商名称**`AAD`和**备注**。

5.  在**元数据文档**区域，单击**上传文件**。

    **说明：** 上传在[步骤2：配置AAD SSO](#section_hcw_ey6_57b)中下载的**联合元数据XML**。

6.  单击**确定**。


## 步骤4：在阿里云创建RAM角色

1.  创建身份提供商后，单击**前往新建RAM角色**。

2.  单击**创建RAM角色**。

3.  选择可信实体类型为**身份提供商**，单击**下一步**。

4.  输入**角色名称**`AADrole`和**备注**。

5.  在下拉列表中选择身份提供商`AAD`，单击**完成**。

    **说明：**

    -   您可以根据需要为RAM角色添加权限。关于如何为RAM角色添加权限，请参见[为RAM角色授权](/intl.zh-CN/角色管理/为RAM角色授权.md)。
    -   当身份提供商和对应的RAM角色创建完成后，请保存好对应的ARN。关于如何查看ARN，请参见[查看RAM角色基本信息](/intl.zh-CN/角色管理/查看RAM角色基本信息.md)。
6.  单击**关闭**。


## 步骤5：将阿里云RAM角色与AAD用户进行关联

1.  在AAD中创建角色。

    1.  管理员用户登录[AAD Graph浏览器](https://developer.microsoft.com/en-us/graph/graph-explorer)。

    2.  单击账号右侧的![settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p139775.png)。

    3.  单击**选择权限**。

    4.  在权限页面，选择以下权限并单击**同意**。

        ![权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p44135.png)

        **说明：** 修改权限后，系统会重定向到Graph浏览器。

    5.  在Graph浏览器页面，第一个下拉列表中选择**GET**，第二个下拉列表中选择**beta**。在搜索框中输入`https://graph.microsoft.com/beta/servicePrincipals/<objectID>`，其中`objectID`是您在AAD属性页面保存的**对象ID**，然后单击**运行查询**。

        **说明：** 如果您有多个目录，您可以在查询区域输入`https://graph.microsoft.com/beta/contoso.com/servicePrincipals`。

    6.  在**响应预览**页签下，提取出`appRoles`属性并保存。

        ```
         "appRoles": [
                        {
                            "allowedMemberTypes": [
                                "User"
                            ],
                            "description": "msiam_access",
                            "displayName": "msiam_access",
                            "id": "7dfd756e-8c27-4472-b2b7-38c17fc5****",
                            "isEnabled": true,
                            "origin": "Application",
                            "value": null
                        }
                    ],
        ```

    7.  返回**Graph浏览器**，将第一个下拉列表改为**PATCH**，第二个下拉列表中选择**beta**。在搜索框中输入`https://graph.microsoft.com/beta/servicePrincipals/<objectID>`，其中`objectID`是您在AAD属性页面保存的**对象ID**，将以下内容复制到**请求正文**中并选择**运行查询**。

        ```
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "7dfd756e-8c27-4472-b2b7-38c17fc5****",
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078c****", //自定义ID
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD" //身份提供商和RAM角色的ARN
            }
          ]
        }
        ```

        **说明：** 您可以根据需要创建多个RAM角色，AAD将在SAML中将这些角色作为声明值进行传送，但是您只能在`msiam_access`后添加新的角色。

2.  将RAM角色添加到用户（u2）中。

    1.  管理员用户登录**Azure门户**。

    2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

    3.  在**名称**列表下，单击**Alibaba Cloud Service \(Role-based SSO\)**。

    4.  在左侧导航栏，单击**用户和组**。

    5.  单击左上角的**添加用户**。

        ![添加用户](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p44178.png)

    6.  单击**用户**，从用户列表中选择用户（u2），单击**选择**。

    7.  单击**分配**。

    8.  查看分配的角色。

        ![查看分配的角色](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5726498951/p44185.png)

        **说明：** 如果您分配了用户（u2），创建的RAM角色会自动附加给用户。如果您创建了多个角色，您需要根据需要合理分配角色。如果您需要完成AAD与多个阿里云账号的角色SSO，请重复上述配置步骤。


## 配置验证

1.  获取用户访问URL。

    1.  管理员用户登录**Azure门户**。

    2.  在左侧导航栏，单击**Azure Active Directory** \> **企业应用程序** \> **所有应用程序**。

    3.  在**名称**列表下，单击**Alibaba Cloud Service \(Role-based SSO\)**。

    4.  在左侧导航栏，选择**属性**，获取**用户访问URL**。

        ![用户访问URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8890507061/p187951.png)

2.  用户（u2）从管理员用户处获取上述**用户访问URL**在浏览器中输入该URL，使用自己的账号登录。

    系统将自动单点登录并重定向到您指定的**中继状态**页面。如果未指定**中继状态**或超出允许范围，则系统会访问如下阿里云控制台首页。

    ![角色SSO成功](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8890507061/p187952.png)


