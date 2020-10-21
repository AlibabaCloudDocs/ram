# Overview of role-based SSO

This topic describes the scenario, process, configuration, and configuration examples of role-based single sign-on \(SSO\).

If Alibaba Cloud and the identity management system of an enterprise work together to implement role-based SSO, Alibaba Cloud is the service provider \(SP\) and the identity management system is the identity provider \(IdP\). Role-based SSO allows the enterprise to manage users in the local IdP without the need to synchronize users from the IdP to Alibaba Cloud. In addition, employees of the enterprise can log on to Alibaba Cloud by using a specific RAM role.

## Process

Role-based SSO allows employees of the enterprise to access Alibaba Cloud by logging on to the Alibaba Cloud Management Console or by using a program.

## Access Alibaba Cloud by using the console

![Access Alibaba Cloud by using the console](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6320549951/p40723.png)

After an administrator configures role-based SSO, the employee \(Alice\) can log on to the Alibaba Cloud Management Console. The following list describes the process:

1.  Alice uses a browser to select Alibaba Cloud as the target service on the logon page of the IdP.

    For example, if the IdP is Microsoft Active Directory Federation Service \(AD FS\), the logon URL is `https://ADFSServiceName/adfs/ls/IdpInitiatedSignOn.aspx`.

    **Note:** Some IdPs require users to first log on and then select the SSO application that represents Alibaba Cloud.

2.  The IdP generates a SAML response and returns it to the browser.

3.  The browser redirects Alice to the SSO service page and forwards the SAML response to the SSO service.

4.  The SSO service uses the SAML response to request an STS token from the Alibaba Cloud STS service. Then, the SSO service generates a URL for Alice to log on to the Alibaba Cloud Management Console by using the STS token.

    **Note:** If the SAML response contains attributes that map to multiple RAM roles, users are prompted to first select a role.

5.  The SSO service returns the URL to the browser.

6.  The browser redirects Alice to the URL, and Alice logs on to the Alibaba Cloud Management Console as the specified role.


## Access Alibaba Cloud by using a program

![Access Alibaba Cloud by using a program](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7320549951/p40724.png)

The following process takes an employee named Alice as an example to describe how to access Alibaba Cloud by using a program.

1.  Alice initiates an authentication request to the IdP by using a program.

2.  The IdP generates a SAML response that contains the SAML assertion, and returns the SAML response to the program.

3.  The program calls the [AssumeRoleWithSAML](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md) API operation of the Alibaba Cloud STS service and forwards the following information: the ARN of the IdP, the ARN of the role to be assumed, and the SAML assertion that is obtained from the IdP.

4.  The STS service verifies the SAML assertion and returns an STS token to the program.

5.  The program calls Alibaba Cloud API operations by using the STS token.


## Configure role-based SSO

Before you implement role-based SSO, you must establish trust between Alibaba Cloud and your IdP.

1.  To make sure that your IdP is trusted by Alibaba Cloud, you must configure the IdP in the Alibaba Cloud Management Console.

    For more information, see [Configure the SAML settings of Alibaba Cloud for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Configure the SAML settings of Alibaba Cloud for role-based SSO.md).

2.  You must use a program or log on to the RAM console to create RAM roles and grant permissions to them.

    For more information, see [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md).

3.  To make sure that Alibaba Cloud is trusted by your IdP, you must configure Alibaba Cloud as a trusted SAML SP and configure SAML assertions in your IdP.

    For more information, see [Configure Alibaba Cloud as a trusted SP for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Configure Alibaba Cloud as a trusted SP for role-based SSO.md).


## Configuration examples

Examples of how to implement role-based SSO to Alibaba Cloud from common enterprise IdPs, such as AD FS, Okta, and Azure AD:

-   [Implement role-based SSO from AD FS](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO from AD FS.md)
-   [Implement role-based SSO from Okta](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO from Okta.md)
-   [Implement role-based SSO from Azure AD](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO from Azure AD.md)

