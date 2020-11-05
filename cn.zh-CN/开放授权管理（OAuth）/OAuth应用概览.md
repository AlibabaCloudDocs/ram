# OAuth应用概览

RAM支持使用OAuth 2.0协议进行用户认证和应用授权。本文介绍OAuth 2.0的基本概念和应用场景。

## OAuth基本概念

|概念|说明|
|--|--|
|用户|用户需要登录到阿里云并授权应用访问阿里云资源。用户可以是阿里云账号（主账号），也可以是RAM用户。|
|阿里云OAuth 2.0服务|对用户进行认证，并接受用户对应用的授权，生成代表用户身份的令牌并返回给被授权的应用。|
|OAuth应用|获取用户授权，并获取代表用户身份的令牌，从而可以访问阿里云。OAuth 2.0服务目前支持的应用类型包括：

-   **WebApp**：指基于浏览器交互的网络应用。
-   **NativeApp**：指操作系统中运行的本地应用，主要为运行在桌面操作系统或移动操作系统中的应用。
-   **ServerApp**：指直接访问阿里云服务，而无需依赖用户登录的应用。目前仅支持基于SCIM协议的用户同步应用。 |
|OAuth范围|OAuth 2.0服务通过OAuth范围来限定应用扮演用户登录阿里云后可以访问的范围。支持的范围如下：

-   openid：用于获取用户的OpenID（默认权限范围，不可移除）。

**说明：** 获取到的OpenID是一个可以唯一代表用户的字符串，但并不包含阿里云UID、用户名等信息。如果需要这些信息，需要使用aliuid、profile等权限范围。

-   aliuid：用于获取阿里云UID。
-   profile：用于获取用户名称等个人信息。
-   /acs/ccc：用于访问阿里云呼叫中心服务API。
-   /acs/alidns：用于访问阿里云解析API。
-   /acs/scim：用于访问阿里云跨域身份管理服务。
-   /acs/digitalstore：用于访问数字化门店（Digital Store）。
-   /acs/scsp：用于访问智能客服平台（Smart Customer Service Platform）。
-   /acs/cloudgame：用于访问云游戏平台（Cloud Gaming Platform）。
-   /acs/aiccs：用于访问智能联络中心。 |
|令牌|OAuth 2.0服务可以给应用下发代表登录用户的令牌。

-   身份令牌：包含用户的身份信息，不能用于访问阿里云资源。
-   访问令牌：包含用户的身份信息以及应用的OAuth范围，可以用于访问OAuth范围内的阿里云资源。
-   刷新令牌：用于换取新的访问令牌。 |
|阿里云API|应用通过调用API可以访问相应资源。|

## OAuth的应用场景

-   [Web应用登录阿里云](/cn.zh-CN/开放授权管理（OAuth）/OAuth应用典型场景/Web应用登录阿里云.md)
-   [Native应用登录阿里云](/cn.zh-CN/开放授权管理（OAuth）/OAuth应用典型场景/Native应用登录阿里云.md)
-   [通过OIDC获取用户信息](/cn.zh-CN/开放授权管理（OAuth）/OAuth应用典型场景/通过OIDC获取用户信息.md)
-   [通过SCIM协议将企业内部账号同步到阿里云RAM](/cn.zh-CN/开放授权管理（OAuth）/OAuth应用典型场景/通过SCIM协议将企业内部账号同步到阿里云RAM.md)

