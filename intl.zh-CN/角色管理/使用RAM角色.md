# 使用RAM角色

本文为您介绍RAM用户如何通过控制台和API扮演受信实体为阿里云账号的RAM角色。

使用RAM角色前，请先完成以下操作：

1.  [创建RAM用户](/intl.zh-CN/用户管理/基本操作/创建RAM用户.md)。
2.  为该RAM用户设置登录密码或创建访问密钥。
    -   关于如何设置登录密码，请参见[修改RAM用户登录密码](/intl.zh-CN/安全设置/密码/修改RAM用户登录密码.md)。
    -   关于如何创建访问密钥，请参见[为RAM用户创建访问密钥](/intl.zh-CN/安全设置/访问密钥/为RAM用户创建访问密钥.md)。
3.  [为RAM用户授权](/intl.zh-CN/用户管理/授权管理/为RAM用户授权.md)。
    -   您可以为RAM用户添加系统策略`AliyunSTSAssumeRoleAccess`。
    -   您也可以为RAM用户添加自定义策略，指定该RAM用户可以扮演哪个RAM角色。更多信息，请参见[能否指定RAM用户具体可以扮演哪个RAM角色？](/intl.zh-CN/常见问题/RAM角色和STS Token常见问题.md)。

## 通过控制台扮演RAM角色

RAM用户或角色SSO登录后，可以通过切换身份的方式扮演RAM角色。

1.  使用RAM用户登录[RAM控制台](https://signin.alibabacloud.com/login.htm)。

2.  将鼠标悬停在右上角头像的位置，查看**企业别名**并保存，然后单击**切换身份**。

3.  在**角色切换**页面，输入企业别名和角色名。

    **说明：** 在**角色切换**页面除了输入企业别名（账号别名），您也可以输入默认域名或阿里云账号（主账号）进行角色切换。关于如何查看默认域名，请参见[查看和修改默认域名](/intl.zh-CN/安全设置/高级设置/查看和修改默认域名.md)。

4.  单击**提交**。

    切换成功后，RAM用户将以RAM角色身份登录控制台，此时RAM用户只能执行该RAM角色身份被授权的所有操作。

    在控制台右上角头像位置将会显示用户的登录身份（即登录时使用的身份，可能是RAM用户，也可能是RAM角色）和当前身份（即切换角色后的身份）。在不同情况下，用户登录身份和当前身份的取值如下表所示：

    |登录方式|登录身份|当前身份|
    |----|----|----|
    |RAM用户|显示格式为<当前登录的RAM用户名称\>。

|显示格式为<RoleName\>/<RoleSessionName\>。

    -   RoleName：当前切换的角色名称。
    -   RoleSessionName：当前登录的RAM用户名称，同登录身份。 |
    |角色SSO|RAM角色第一次登录（指通过角色SSO直接登录）后，只显示当前身份，不显示登录身份。

RAM角色登录（指通过角色SSO直接登录）后再次切换身份后，登录身份显示角色SSO的身份信息，显示格式为<RoleName\>/<RoleSessionName\>。

    -   RoleName：角色SSO登录时的角色名称。
    -   RoleSessionName：角色SSO登录时的RoleSessionName。
例如：外部IdP中的用户tom@example.local通过RAM角色test-saml-role1登录到控制台，然后再次使用角色alice-testrole切换身份，切换后显示登录身份为test-saml-role1/tom@example.local。

|显示格式为<RoleName\>/<RoleSessionName\>。

    -   RoleName：当前切换的角色名称。
    -   RoleSessionName：角色SSO登录时的RoleSessionName。
例如：外部IdP中的用户tom@example.local通过RAM角色test-saml-role1登录到控制台，这时当前身份为test-saml-role1/tom@example.local，然后再次使用角色alice-testrole切换身份，此次当前身份为alice-testrole/tom@example.local，其中RoleSessionName保持不变。 |

    角色登录会话有效期将以角色**最大会话时间**与**登录Session过期时间**中设置的较小值为准。更多信息，请参见[设置角色最大会话时间](/intl.zh-CN/角色管理/设置角色最大会话时间.md)、[设置RAM用户安全策略](/intl.zh-CN/安全设置/基本安全设置/设置RAM用户安全策略.md)。


## 通过调用API扮演RAM角色

有权限的RAM用户可以使用其访问密钥调用[AssumeRole](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md) API，以获取某个RAM角色的安全令牌（STS Token），从而使用安全令牌访问阿里云。

**说明：** 如果您通过扮演角色获取的STS Token发生泄漏，您可以回收所有已经颁发的STS Token。具体操作，请参见[STS Token发生泄漏时如何处理？](/intl.zh-CN/常见问题/RAM角色和STS Token常见问题.md)。

## 相关链接

您也可以通过角色SSO登录控制台。更多信息，请参见[角色SSO概览](/intl.zh-CN/单点登录管理（SSO）/角色SSO/角色SSO概览.md)。

