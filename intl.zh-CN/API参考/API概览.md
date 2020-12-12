# API概览

请根据使用场景选择对应的API。

|场景|描述|API选型|API区别|
|--|--|-----|-----|
|用户管理|管理RAM用户、访问密钥（AccessKey）、登录密码、多因素认证设备（MFA）。|-   [IMS API](/intl.zh-CN/API参考/API 参考（IMS）/API概览.md)
-   [RAM API](/intl.zh-CN/API参考/API参考（RAM）/API概览.md)

|-   RAM API与IMS API中存在部分相同的API，其功能是相同的，支持混用。
-   IMS API支持更多的新功能，例如：查询访问密钥最后使用时间、修改默认域名、获取用户凭证报告等。
-   后续用户管理、用户组管理和安全设置的新功能都将体现在IMS API中，所以推荐您使用IMS API。 |
|用户组管理|管理RAM用户组，并在RAM用户组中添加或移除RAM用户。|
|安全设置|管理密码强度策略、全局安全首选项、默认域名、用户凭证报告和账号安全报告。|
|权限策略管理|管理权限策略，并为RAM用户、RAM角色和RAM用户组添加或移除权限。|-   [RAM API](/intl.zh-CN/API参考/API参考（RAM）/API概览.md)
-   [资源管理API]()

|-   RAM API与资源管理API中存在部分相同的API，其功能是相同的，支持混用。
-   资源管理API支持对资源组授权，RAM API不支持。
-   资源管理API支持更多的新功能，例如：服务关联角色。
-   资源管理API使用更加方便，例如：您使用AttachPolicy一个API就可以为RAM用户、RAM角色或RAM用户组分别添加权限。
-   后续权限策略管理和角色管理的新功能都将体现在资源管理API中，所以推荐您使用资源管理API。 |
|角色管理|管理RAM角色。|
|角色使用|使用STS Token进行角色扮演。|[STS API](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md)|无|
|单点登录（SSO）管理|管理进行用户SSO和角色SSO时的身份提供商。|[IMS API](/intl.zh-CN/API参考/API 参考（IMS）/API概览.md)|无|
|角色SSO使用|使用STS Token进行角色SSO登录。|[STS API](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRoleWithSAML.md)|无|
|开放授权（OAuth）管理|管理应用、应用密钥。|[IMS API](/intl.zh-CN/API参考/API 参考（IMS）/API概览.md)|无|

