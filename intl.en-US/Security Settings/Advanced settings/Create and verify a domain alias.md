# Create and verify a domain alias

This topic describes how to create and verify a domain alias for an Alibaba Cloud account. A domain alias is an alias of your default domain name. After you create and verify a domain alias, RAM users of the Alibaba Cloud account can use this domain alias to log on to the RAM console.

The domain alias must be publicly resolvable. Before the domain alias can be used, you must verify that you own the domain alias.

1.  Create a domain alias in the RAM console.

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with your Alibaba Cloud account.

    2.  In the left-side navigation pane, click **Settings** under **Identities**.

    3.  On the **Advanced** tab, click **Create Domain Alias**.

    4.  Set the **Domain Name** parameter.

    5.  Click **OK** and then copy the verification code.

2.  Add a TXT record in the system at your DNS hosting provider.

    If you use the Alibaba Cloud DNS service, configure the TXT record, as shown in the following figure. Note that you must enter the verification code in the **Value** field. For more information, see [Add DNS records](https://www.alibabacloud.com/help/zh/faq-detail/29725.html).

    ![Add a TXT record](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9500788951/p131551.png)

3.  Log on to the RAM console to verify that you own the domain name.

    1.  In the left-side navigation pane, click **Settings** under **Identities**.

    2.  On the **Advanced** tab, click **Domain Ownership Verification**.

    3.  Click **OK**.


After the domain alias is created, the RAM users of your Alibaba Cloud account can use the domain alias to log on to the [RAM console](https://signin.alibabacloud.com/login.htm).

The logon name of a RAM user follows the format of `<$username>@<$DomainAlias>`. For more information, see [Log on to the console as a RAM user](/intl.en-US/RAM User Management/Log on to the console as a RAM user.md).

You can use the domain alias to simplify the procedure of configuring user-based SSO. For more information, see [Configure the SAML settings of Alibaba Cloud for user-based SSO](/intl.en-US/SSO Management/User-based SSO/Configure the SAML settings of Alibaba Cloud for user-based SSO.md).

