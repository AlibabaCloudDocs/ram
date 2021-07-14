# Configure the SAML settings of Alibaba Cloud for role-based SSO

This topic describes how to configure metadata for role-based single sign-on \(SSO\) to make sure that your identity provider \(IdP\) is trusted by Alibaba Cloud \(service provider\).

The metadata file of your IdP is obtained. The metadata file is in the XML format. The metadata file contains the logon URLs, the public key that is used to verify SAML assertions, and the assertion format.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** tab of the page that appears, click **Create IdP**.

4.  In the Create IdP panel, configure **IdP Name** and **Note**.

5.  In the **Metadata File** section, click **Upload** to upload the metadata file that is obtained from your IdP.

6.  Click **OK**.


On the page that appears, click **Create RAM Role** to create RAM roles based on your business requirements. For more information, see [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md).

