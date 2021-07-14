# Create and verify a domain alias

This topic describes how to create and verify a domain alias for an Alibaba Cloud account. A domain alias is an alias of your default domain name. After you create and verify a domain alias, Resource Access Management \(RAM\) users of the Alibaba Cloud account can use this domain alias to log on to the RAM console.

You own a domain name that is publicly resolvable.

1.  Create a domain alias in the RAM console.

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

    2.  In the left-side navigation pane, choose **Identities** \> **Settings**.

    3.  On the Settings page, click the **Advanced** tab.

    4.  In the **Domain Alias** section, click **Create Domain Alias**.

    5.  In the Create Domain Alias panel, specify **Domain Name** and click **OK**.

    6.  Copy the verification code.

2.  Add a TXT record in the system of your DNS service provider.

    If you use Alibaba Cloud DNS, configure the TXT record in the Alibaba Cloud DNS console. You must enter the verification code that you copied in Step [1](#step_i79_zjw_ai1) in the **Value** field. For more information, see [Add DNS records](https://www.alibabacloud.com/help/faq-detail/29725.html).

    ![Add a TXT record](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9500788951/p131551.png)

3.  Log on to the RAM console to verify the ownership of the domain name.

    1.  In the left-side navigation pane, choose **Identities** \> **Settings**.

    2.  In the **Domain Alias** section of the **Advanced** tab, click **Domain Ownership Verification**.

    3.  In the Verify Domain Ownership message, view the verification result and click **OK**.


After the domain alias is created, the RAM users of your Alibaba Cloud account can use the domain alias to log on to the [RAM console](https://signin.alibabacloud.com/login.htm). The logon name of a RAM user follows the format of `<UserName>@<DomainAlias>`. For more information, see [Log on to the console as a RAM user](/intl.en-US/RAM User Management/Logon management/Log on to the console as a RAM user.md).

You can use the domain alias to simplify the procedure of configuring user-based single sign-on \(SSO\). For more information, see [Configure the SAML settings of Alibaba Cloud for user-based SSO](/intl.en-US/SSO Management/User-based SSO/Configure the SAML settings of Alibaba Cloud for user-based SSO.md).

