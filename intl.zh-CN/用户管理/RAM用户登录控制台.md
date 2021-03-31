# RAM用户登录控制台

本文为您介绍RAM用户如何登录阿里云控制台，包括登录地址和登录方式。

-   默认域名、账号别名、域别名的概念，请参见[基本概念](/intl.zh-CN/产品简介/基本概念.md)。
-   阿里云账号登录RAM控制台后，在**人员管理** \> **设置** \> **高级设置**中查看默认域名和域别名。

1.  RAM用户登录[阿里云控制台](https://signin.alibabacloud.com/login.htm)。

    **说明：** 阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)，在概览页可以快速查询RAM用户的登录地址。

2.  输入RAM用户的登录名称，单击**下一步**。

    -   方式一：使用默认域名登录。RAM用户的登录格式为`<$username>@<$AccountAlias>.onaliyun.com`，例如：username@company-alias.onaliyun.com。

        **说明：** RAM用户的登录账号为UPN（User Principal Name）格式，即RAM控制台用户列表中所见的用户登录名称。<$username\> 为RAM用户名称，<$AccountAlias\>.onaliyun.com 为默认域名。

    -   方式二：使用账号别名登录。RAM用户的登录格式为`<$username>@<$AccountAlias>`，例如：username@company-alias。

        **说明：** <$username\> 为RAM用户名称，<$AccountAlias\> 为账号别名。

    -   方式三：如果创建了域别名，也可以使用域别名登录。RAM用户的登录格式为`<$username>@<$DomainAlias>`，例如：username@example.com。

        **说明：** <$username\>为RAM用户名称，<$DomainAlias\>为域别名。

3.  输入RAM用户的登录密码，单击**登录**。

4.  （可选）如果您开启了多因素认证（MFA），则需要输入虚拟MFA设备生成的验证码，或通过U2F安全密钥认证。

    更多信息，请参见[多因素认证（MFA）](/intl.zh-CN/安全设置/安全设置概览.md)和[为RAM用户启用多因素认证](/intl.zh-CN/安全设置/多因素认证/为RAM用户启用多因素认证.md)。


