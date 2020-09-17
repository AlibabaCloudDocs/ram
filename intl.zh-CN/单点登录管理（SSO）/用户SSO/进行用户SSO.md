# 进行用户SSO

本文为您介绍用户SSO的背景、基本流程、配置步骤及配置示例。

阿里云与企业进行用户SSO时，阿里云是服务提供商（SP），而企业自有的身份管理系统则是身份提供商（IdP）。通过用户SSO，企业员工在登录后，将以RAM用户身份访问阿里云。

## 基本流程

![用户SSO基本流程](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5965217951/p40784.png)

当管理员在完成用户SSO的相关配置后，企业员工Alice可以通过如图所示的方法登录到阿里云。

1.  Alice使用浏览器登录阿里云，阿里云将SAML认证请求返回给浏览器。

2.  浏览器向IdP转发SAML认证请求。

3.  IdP提示Alice登录，并在Alice登录成功后生成SAML响应返回给浏览器。

4.  浏览器将SAML响应转发给SSO服务。

5.  SSO服务通过SAML互信配置，验证SAML响应的数字签名来判断SAML断言的真伪，并通过SAML断言的`NameID`元素值，匹配到对应阿里云账号中的RAM用户身份。

6.  SSO服务向浏览器返回控制台的URL。

7.  浏览器重定向到阿里云控制台。

    **说明：** 在第1步中，企业员工从阿里云发起登录并不是必须的。企业员工也可以在企业自有IdP的登录页直接点击登录到阿里云的链接，向企业IdP发出登录到阿里云的SAML认证请求。


## 配置步骤

为了建立阿里云与企业IdP之间的互信关系，需要进行阿里云作为SP的SAML配置和企业IdP的SAML配置，配置完成后才能进行用户SSO。

1.  为了建立阿里云对企业IdP的信任，需要将企业IdP配置到阿里云。

    详情请参见[进行用户SSO时阿里云SP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/用户SSO/进行用户SSO时阿里云SP的SAML配置.md)。

2.  为了建立企业IdP对阿里云的信任，需要在企业IdP中配置阿里云为可信SAML SP并进行SAML断言属性的配置。

    详情请参见[进行用户SSO时企业IdP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/用户SSO/进行用户SSO时企业IdP的SAML配置.md)。

3.  企业IdP和阿里云均配置完成后，企业需要使用SDK、CLI或登录到RAM控制台创建与企业IdP匹配的RAM用户。

    详情请参见[创建RAM用户](/intl.zh-CN/用户管理/创建RAM用户.md)。


## 配置示例

如下为您提供了常见的企业IdP（例如：AD FS、Okta和Azure AD）与阿里云进行用户SSO的配置示例：

-   [使用AD FS进行用户SSO的示例](/intl.zh-CN/单点登录管理（SSO）/用户SSO/使用AD FS进行用户SSO的示例.md)
-   [使用Okta进行用户SSO的示例](/intl.zh-CN/单点登录管理（SSO）/用户SSO/使用Okta进行用户SSO的示例.md)
-   [使用Azure AD进行用户SSO的示例](/intl.zh-CN/单点登录管理（SSO）/用户SSO/使用Azure AD进行用户SSO的示例.md)

