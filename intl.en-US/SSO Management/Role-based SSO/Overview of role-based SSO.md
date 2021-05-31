# Overview of role-based SSO

If Alibaba Cloud and the identity management system of an enterprise work together to implement role-based single sign-on \(SSO\), Alibaba Cloud is the service provider \(SP\) and the identity management system is the identity provider \(IdP\). Role-based SSO allows the enterprise to manage users in the local IdP without the need to synchronize users from the IdP to Alibaba Cloud. In addition, employees of the enterprise can access Alibaba Cloud by using a specific RAM role.

## Process

Role-based SSO allows employees of the enterprise to access Alibaba Cloud by logging on to the Alibaba Cloud Management Console or by using a program.

-   **Access Alibaba Cloud by logging on to the Alibaba Cloud Management Console**

    The following figure shows how Alice, an employee, accesses Alibaba Cloud by logging on to the Alibaba Cloud Management Console after an administrator configures role-based SSO.

    ![Access Alibaba Cloud by logging on to the Alibaba Cloud Management Console](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8092542261/p40723.png)

    The following list describes the process:

    1.  Alice opens the logon page of the IdP on a browser and selects Alibaba Cloud as the required service.

        In this example, the IdP is Microsoft Active Directory Federation Services \(AD FS\). Therefore, the logon URL is `https://ADFSServiceName/adfs/ls/IdpInitiatedSignOn.aspx`.

        **Note:** Some IdPs require users to log on before users select the SSO application that represents Alibaba Cloud.

    2.  The IdP generates a Security Assertion Markup Language \(SAML\) response and returns the response to the browser.
    3.  The browser redirects Alice to the SSO service page and forwards the SAML response to the SSO service.
    4.  The SSO service uses the SAML response to request an STS token from the Alibaba Cloud STS service. Then, the SSO service generates a URL that Alice can use to log on to the Alibaba Cloud Management Console by using the STS token.

        **Note:** If the SAML response contains attributes that map to multiple RAM roles, Alice is prompted to first select a role.

    5.  The SSO service returns the URL to the browser.
    6.  The browser redirects Alice to the URL, and Alice logs on to the Alibaba Cloud Management Console as the specified role.
-   **Access Alibaba Cloud by using a program**

    The following figure shows how Alice accesses Alibaba Cloud by using a program.

    ![Access Alibaba Cloud by using a program](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8092542261/p40724.png)

    The following list describes the process:

    1.  Alice initiates a logon request to the IdP by using a program.
    2.  The IdP generates an SAML response that contains the SAML assertion and returns the SAML response to the program.
    3.  The program calls the [AssumeRoleWithSAML](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRoleWithSAML.md) operation of the Alibaba Cloud STS service and forwards the following information:

        The Alibaba Cloud Resource Name \(ARN\) of the IdP, the ARN of the role to be assumed, and the SAML assertion that is obtained from the IdP

    4.  The STS service verifies the SAML assertion and returns an STS token to the program.
    5.  The program calls Alibaba Cloud API operations by using the STS token.

## Configure role-based SSO

Before you can implement role-based SSO, you must establish trust between Alibaba Cloud and your IdP.

1.  Configure the IdP in the Alibaba Cloud Management Console to ensure that your IdP is trusted by Alibaba Cloud.

    For more information, see [Configure the SAML settings of Alibaba Cloud for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Configure the SAML settings of Alibaba Cloud for role-based SSO.md).

2.  Use a program or log on to the RAM console to create RAM roles for role-based SSO and grant permissions to the RAM roles.

    For more information, see [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md).

3.  Configure Alibaba Cloud as a trusted SAML SP and configure SAML assertions in your IdP to make sure that Alibaba Cloud is trusted by your IdP.

    For more information, see [Configure Alibaba Cloud as a trusted SP for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Configure Alibaba Cloud as a trusted SP for role-based SSO.md).


## Examples

The following list provides examples of how to implement role-based SSO to Alibaba Cloud from common enterprise IdPs, such as AD FS, Okta, and Azure AD:

-   [Implement role-based SSO by using Active Directory Federation Services](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO by using Active Directory Federation Services.md)
-   [Implement role-based SSO from Okta](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO from Okta.md)
-   [Implement role-based SSO by using Azure Active Directory](/intl.en-US/SSO Management/Role-based SSO/Implement role-based SSO by using Azure Active Directory.md)

