# Overview of user-based SSO

This topic describes the scenario, process, configuration, and configuration examples of user-based single sign-on \(SSO\).

If Alibaba Cloud and the identity management system of an enterprise work together to implement user-based SSO, Alibaba Cloud is the service provider \(SP\) and the enterprise is the identity provider \(IdP\). User-based SSO allows an employee of the enterprise to access Alibaba Cloud resources as a RAM user.

## Process

![Process](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5220549951/p40784.png)

After an administrator configures user-based SSO, the employee \(Alice\) can log on to the Alibaba Cloud Management Console. The following list describes the process:

1.  Alice uses a browser to log on to the Alibaba Cloud Management Console. Then, Alibaba Cloud returns a SAML authentication request to the browser.

2.  The browser forwards the SAML authentication request to the IdP.

3.  Alice is prompted to log on to the IdP portal. After Alice logs on to the IdP portal, the IdP returns a SAML response to the browser.

4.  The browser forwards the SAML response to the SSO service.

5.  Based on the SAML mutual trust configuration, the SSO service verifies the digital signature in the SAML response to check the authenticity of the SAML assertion. Then, the SSO service maps the value of the `NameID` element in the SAML assertion to the RAM user identity in Alibaba Cloud.

6.  The SSO service returns the URL of the Alibaba Cloud Management Console to the browser.

7.  The browser redirects Alice to the Alibaba Cloud Management Console.

    **Note:** In Step 1, Alice does not need to initiate the logon from Alibaba Cloud. Instead, Alice can click the Alibaba Cloud logon URL in the IdP portal to send a SAML authentication request to the IdP.


## Configuration

Before you implement user-based SSO, you must establish trust between Alibaba Cloud and your IdP.

1.  To make sure that your IdP is trusted by Alibaba Cloud, you must configure the IdP in the Alibaba Cloud Management Console.

    For more information, see [Configure the SAML settings of Alibaba Cloud for user-based SSO](/intl.en-US/SSO Management/User-based SSO/Configure the SAML settings of Alibaba Cloud for user-based SSO.md).

2.  To make sure that Alibaba Cloud is trusted by your IdP, you must configure Alibaba Cloud as a trusted SAML SP and configure SAML assertions in your IdP.

    For more information, see [Configure Alibaba Cloud as a trusted SP for user-based SSO](/intl.en-US/SSO Management/User-based SSO/Configure Alibaba Cloud as a trusted SP for user-based SSO.md).

3.  After the IdP and Alibaba Cloud SAML settings are configured, you must create RAM users that correspond to the users in the IdP by using the software development kit \(SDK\), command line interface \(CLI\), or RAM console.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).


## Configuration example

Examples of how to implement user-based SSO to Alibaba Cloud from common enterprise IdPs, such as AD FS, Okta, and Azure AD:

-   [Implement user-based SSO from AD FS](/intl.en-US/SSO Management/User-based SSO/Implement user-based SSO from AD FS.md)
-   [Implement user-based SSO from Okta](/intl.en-US/SSO Management/User-based SSO/Implement user-based SSO from Okta.md)
-   [Implement user-based SSO from Azure AD](/intl.en-US/SSO Management/User-based SSO/Implement user-based SSO from Azure AD.md)

