# 角色SSO概览

阿里云与企业进行角色SSO时，阿里云是服务提供商（SP），而企业自有的身份管理系统则是身份提供商（IdP）。通过角色SSO，企业可以在本地IdP中管理员工信息，无需进行阿里云和企业IdP间的用户同步，企业员工将使用指定的RAM角色登录阿里云。

## 基本流程

企业员工可以通过控制台或程序访问阿里云。

-   **通过控制台访问阿里云**

    当管理员在完成角色SSO的相关配置后，企业员工Alice可以通过如下图所示的方法登录到阿里云。

    ![通过控制台访问阿里云](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5288139161/p40723.png)

    操作步骤：

    1.  Alice使用浏览器在IdP的登录页面中选择阿里云作为目标服务。

        例如：如果企业IdP使用AD FS（Microsoft Active Directory Federation Service），则登录URL为：`https://ADFSServiceName/adfs/ls/IdpInitiatedSignOn.aspx`。

        **说明：** 有些IdP会要求用户先登录，再选择代表阿里云的SSO应用。

    2.  IdP生成一个SAML响应并返回给浏览器。
    3.  浏览器重定向到SSO服务页面，并转发SAML响应给SSO服务。
    4.  SSO服务使用SAML响应向阿里云STS服务请求临时安全凭证，并生成一个可以使用临时安全凭证登录阿里云控制台的URL。

        **说明：** 如果SAML响应中包含映射到多个RAM角色的属性，系统将会首先提示用户选择一个用于访问阿里云的角色。

    5.  SSO服务将URL返回给浏览器。
    6.  浏览器重定向到该URL，以指定RAM角色登录到阿里云控制台。
-   **通过程序访问阿里云**

    企业员工Alice可以通过编写程序来访问阿里云，基本流程如下图所示。

    ![使用程序访问阿里云](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5288139161/p40724.png)

    操作步骤：

    1.  Alice使用程序向企业IdP发起登录请求。
    2.  IdP生成一个SAML响应，其中包含关于登录用户的SAML断言，并将此响应返回给程序。
    3.  程序调用阿里云STS服务提供的API [AssumeRoleWithSAML](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRoleWithSAML.md)，并传递以下信息：

        阿里云中身份提供商的ARN、要扮演的角色的ARN以及来自企业IdP的SAML断言。

    4.  STS服务将校验SAML断言并返回临时安全凭证给程序。
    5.  程序使用临时安全凭证调用阿里云API。

## 配置步骤

为了建立阿里云与企业IdP之间的互信关系，需要进行阿里云作为SP的SAML配置和企业IdP的SAML配置，配置完成后才能进行角色SSO。

1.  为了建立阿里云对企业IdP的信任，需要将企业IdP配置到阿里云。

    更多信息，请参见[进行角色SSO时阿里云SP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/角色SSO/进行角色SSO时阿里云SP的SAML配置.md)。

2.  企业需要RAM控制台或程序创建用于SSO的RAM角色，并授予相关权限。

    更多信息，请参见[创建可信实体为身份提供商的RAM角色](/intl.zh-CN/角色管理/创建RAM角色/创建可信实体为身份提供商的RAM角色.md)。

3.  为了建立企业IdP对阿里云的信任，需要在企业IdP中配置阿里云为可信SAML SP并进行SAML断言属性的配置。

    更多信息，请参见[进行角色SSO时企业IdP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/角色SSO/进行角色SSO时企业IdP的SAML配置.md)。


## 配置示例

以下为您提供了常见的企业IdP（例如：AD FS、Okta、Azure AD和OneLogin）与阿里云进行角色SSO的配置示例：

-   [使用AD FS进行角色SSO的示例](/intl.zh-CN/单点登录管理（SSO）/角色SSO/使用AD FS进行角色SSO的示例.md)
-   [使用Okta进行角色SSO的示例](/intl.zh-CN/单点登录管理（SSO）/角色SSO/使用Okta进行角色SSO的示例.md)
-   [使用Azure AD进行角色SSO的示例](/intl.zh-CN/单点登录管理（SSO）/角色SSO/使用Azure AD进行角色SSO的示例.md)
-   [使用OneLogin进行角色SSO的示例](/intl.zh-CN/单点登录管理（SSO）/角色SSO/使用OneLogin进行角色SSO的示例.md)

