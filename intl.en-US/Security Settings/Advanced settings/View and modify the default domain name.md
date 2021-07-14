# View and modify the default domain name

Each Alibaba Cloud account has a default domain name. Resource Access Management \(RAM\) users can use this default domain name as the suffix of their logon name to log on to the Alibaba Cloud Management Console. This topic describes how to view and modify the default domain name.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Settings**.

3.  On the page that appears, click the **Advanced** tab to view and modify the default domain name in the **Default Domain** section.

    -   View the information about the default domain name. The information includes the domain name, status, and the time when the default domain name was created. The default domain name is in the `<AccountAlias>.onaliyun.com` format. `<AccountAlias>` indicates the account alias. The default value of AccountAlias is the ID of your Alibaba Cloud account. In this case, the default domain name is `<AccountID>.onaliyun.com`.
    -   Modify the default domain name. To modify the default domain name, click **Edit**. In the Edit default domain panel, specify an account alias and click **OK**.

The RAM users of your Alibaba Cloud account can use the default domain name to log on to the [RAM console](https://signin.alibabacloud.com/login.htm). To log on to the RAM console, specify the logon name in the format of `<UserName>@<AccountAlias>.onaliyun.com`.`` For more information, see [Log on to the console as a RAM user](/intl.en-US/RAM User Management/Logon management/Log on to the console as a RAM user.md).

The use of default domain names simplifies the procedure to configure SAML for user-based SSO. For more information, see [Configure the SAML settings of Alibaba Cloud for user-based SSO](/intl.en-US/SSO Management/User-based SSO/Configure the SAML settings of Alibaba Cloud for user-based SSO.md).

