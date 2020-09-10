# SSO概览

阿里云支持基于SAML 2.0的SSO（Single Sign On，单点登录），也称为身份联合登录。本文为您介绍企业如何使用自有的身份系统实现与阿里云的SSO。

## SSO基本概念

阿里云提供基于SAML 2.0协议的SSO。为了更好的理解SSO，下面简要介绍与SAML/SSO相关的一些基本概念。

|概念|说明|
|--|--|
|身份提供商（IdP）|一个包含有关外部身份提供商元数据的RAM实体，身份提供商可以提供身份管理服务。

 -   企业本地IdP：Microsoft Active Directory Federation Service （AD FS）、Shibboleth等。
-   Cloud IdP：Azure AD、Google G Suite、Okta、OneLogin等。 |
|服务提供商（SP）|利用IdP的身份管理功能，为用户提供具体服务的应用，SP会使用IdP提供的用户信息。一些非SAML协议的身份系统（例如：OpenID Connect），也把服务提供商称作IdP的信赖方。|
|安全断言标记语言（SAML 2.0）|实现企业级用户身份认证的标准协议，它是SP和IdP之间实现沟通的技术实现方式之一。SAML 2.0已经是目前实现企业级SSO的一种事实标准。|
|SAML断言（SAML assertion）|SAML协议中用来描述认证请求和认证响应的核心元素。例如：用户的具体属性就包含在认证响应的断言里。|
|信赖（Trust）|建立在SP和IdP之间的互信机制，通常由公钥和私钥来实现。SP通过可信的方式获取IdP的SAML元数据，元数据中包含IdP签发SAML断言的签名验证公钥，SP则使用公钥来验证断言的完整性。|

## SSO的方式

企业根据自身需要，使用支持SAML 2.0的企业IdP（例如：AD FS）与阿里云进行SSO。阿里云提供以下两种基于SAML 2.0协议的SSO方式：

-   用户SSO：阿里云通过IdP颁发的SAML断言确定企业用户与阿里云RAM用户的对应关系 。企业用户登录后，使用该RAM用户访问阿里云。请参见[进行用户SSO](/intl.zh-CN/单点登录管理（SSO）/用户SSO/进行用户SSO.md)。
-   角色SSO：阿里云通过IdP颁发的SAML断言确定企业用户在阿里云上可以使用的RAM角色。企业用户登录后，使用SAML断言中指定的RAM角色访问阿里云。请参见[进行角色SSO](/intl.zh-CN/单点登录管理（SSO）/角色SSO/进行角色SSO.md)。

## SSO方式的比较

|SSO方式|SP发起的SSO|IdP发起的SSO|使用RAM用户账号和密码登录|一次性配置IdP关联多个阿里云账号|多个IdP|
|:----|:-------|:--------|:-------------|:----------------|:----|
|用户SSO|支持|支持|不支持|不支持|不支持|
|角色SSO|不支持|支持|支持|支持|支持|

**说明：** 关于用户SSO与角色SSO的更多比较，请参见[SSO方式的适用场景](/intl.zh-CN/单点登录管理（SSO）/SSO方式的适用场景.md)。

