# SSO overview

Alibaba Cloud supports SAML 2.0-based single sign-on \(SSO\), which is also known as identity federation. This topic explains terms that are related to SSO, and describes how to implement SSO between an enterprise identity management system and Alibaba Cloud.

## Terms

Alibaba Cloud supports SAML 2.0-based SSO. This section explains the terms that are related to SAML and SSO.

|Term|Description|
|----|-----------|
|identity provider \(IdP\)|A RAM entity that provides identity management services. IdPs are classified into the following types:

-   IdPs that use the on-premises architecture, such as Microsoft Active Directory Federation Service \(AD FS\) and Shibboleth
-   IdPs that use the cloud-based architecture, such as Azure AD, Google G Suite, Okta, and OneLogin |
|service provider \(SP\)|An application that uses the identity management feature of an IdP to provide users with specific services. An SP uses the user information that is provided by an IdP. In some identity management systems \(such as OpenID Connect\) that do not comply with the SAML protocol, SP is known as the relying party of an IdP.|
|Security Assertion Markup Language 2.0 \(SAML 2.0\)|A protocol that is designed for enterprise-level user identity authentication. SAML 2.0 is used for communication between an SP and an IdP. SAML 2.0 is a standard that enterprises use to implement enterprise-level SSO.|
|SAML assertion|A core element that is defined in the SAML protocol. This element describes the authentication request and response. For example, the SAML assertion for an authentication response can contain user attributes.|
|trust|A mutual trust relationship between an SP and an IdP. In most cases, the trust relationship is established by using public and private keys. An SP can obtain the SAML metadata of a trusted IdP. The metadata includes a public key. The SP uses the public key to verify the integrity of the SAML assertion that is issued by the IdP.|

## SSO methods

You can implement SSO between Alibaba Cloud and your IdP, such as Microsoft Active Directory Federation Service \(AD FS\), based on SAML 2.0. Alibaba Cloud provides the following two SAML 2.0-based SSO methods:

-   User-based SSO: The RAM user identity that you can use to log on to the Alibaba Cloud Management Console is determined based on an SAML assertion. After you log on to the Alibaba Cloud Management Console, you can access Alibaba Cloud resources as a RAM user. For more information, see [Overview of user-based SSO](/intl.en-US/SSO Management/User-based SSO/Overview of user-based SSO.md).
-   Role-based SSO: The RAM role that you can use to log on to the Alibaba Cloud Management Console is determined based on an SAML assertion. After you log on to the Alibaba Cloud Management Console, you can use the RAM role that is specified in the SAML assertion to access Alibaba Cloud resources. For more information, see [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md).

## Comparison between role-based SSO and user-based SSO

|SSO method|SP-initiated SSO|IdP-initiated SSO|Logon with logon names and passwords of RAM users|Association of multiple Alibaba Cloud accounts with a single IdP|Multiple IdPs|
|:---------|:---------------|:----------------|:------------------------------------------------|:---------------------------------------------------------------|:------------|
|User-based SSO|Supported|Supported|Not supported|Not supported|Not supported|
|Role-based SSO|Not supported|Supported|Supported|Supported|Supported|

**Note:** For more information about the differences between these two SSO methods, see [Scenarios of SSO](/intl.en-US/SSO Management/Scenarios of SSO.md).

