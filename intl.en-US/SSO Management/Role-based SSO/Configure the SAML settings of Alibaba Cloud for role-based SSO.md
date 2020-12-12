# Configure the SAML settings of Alibaba Cloud for role-based SSO

This topic describes how to configure metadata for role-based single sign-on \(SSO\) based on SAML 2.0 to establish trust between your identity provider \(IdP\) and Alibaba Cloud \(service provider\).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** tab of the page that appears, click **Create IdP**.

4.  In the panel that appears, specify **IdP Name** and **Note**.

5.  Click **Upload** under **Metadata File** to upload the SAML metadata file.

    **Note:** The SAML metadata file is provided by your IdP. The file is typically in the XML format and contains the logon URLs, public key used to verify SAML assertions, and assertion format.

6.  Click **OK**.


On the page that appears, click **Create RAM Role** to create RAM roles based on your business requirements. For more information, see [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md).

