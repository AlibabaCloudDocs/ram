# Configure Alibaba Cloud as a trusted SP for role-based SSO

This topic describes how to configure Alibaba Cloud as a trusted SAML service provider \(SP\) of your identity provider \(IdP\) for role-based single sign-on \(SSO\).

1.  Find the SAML SP metadata URL of Alibaba Cloud in the RAM console: `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

    2.  In the left-side navigation pane, click **SSO**.

    3.  On the **Role-based SSO** tab, copy the SAML SP metadata URL.

2.  Create a SAML SP in your IdP and configure Alibaba Cloud as the relying party by using one of the following methods:

    -   Use the SAML SP metadata URL of Alibaba Cloud that you copied in the previous step.
    -   If your IdP does not support the URL-based configuration of the relying party, download the metadata file from the URL and upload the metadata file.
    -   If your IdP does not allow you to upload the metadata file, set the following parameters:
        -   `Entity ID`: `urn:alibaba:cloudcomputing:international`.
        -   `ACS URL`: `https://signin.alibabacloud.com/saml-role/sso`.
        -   `RelayState`: Optional. If your IdP requires the `RelayState` parameter, set the parameter to a URL. Users will be redirected to the URL after SSO succeeds. If the parameter is unspecified, users will be redirected to the homepage of the Alibaba Cloud Management Console after SSO succeeds.

            **Note:** You must set the `RelayState` parameter to a URL that points to an Alibaba website. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, and \*.alipay.com.


After you configure Alibaba Cloud as a trusted SAML SP, you must configure SAML assertions at your IdP. For more information, see [SAML response for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/SAML assertions for role-based SSO.md).

