# Configure Alibaba Cloud as a trusted SP for user-based SSO

This topic describes how to configure Alibaba Cloud as a trusted SAML service provider \(SP\) of your identity provider \(IdP\) for user-based single sign-on \(SSO\).

1.  Obtain the SAML SP metadata URL from the Resource Access Management \(RAM\) console.

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

    2.  In the left-side navigation pane, click **SSO**.

    3.  On the SSO page, click the **User-based SSO** tab.

    4.  In the **SSO Settings** section, copy the value of the **SAML Service Provider Metadata URL** parameter.

2.  Create a SAML SP in your IdP and configure Alibaba Cloud as the relying party by using one of the following methods:

    -   Use the SAML SP metadata URL of Alibaba Cloud that you copied in Step [1](#step_45v_415_rxu).
    -   If your IdP does not support the URL-based configuration of the relying party, download the metadata file from the URL that you copied in Step [1](#step_45v_415_rxu) and upload the metadata file.
    -   If your IdP does not allow you to upload the metadata file, configure the following parameters:
        -   `Entity ID`: the value of the `entityID` attribute in the `md:EntityDescriptor` element of the metadata file.
        -   `ACS URL`: the value of the `Location` attribute in the `md:AssertionConsumerService` element of the metadata file.
        -   `RelayState`: This parameter is optional. If your IdP requires the `RelayState` parameter, set the value of the parameter to a URL. Users will be redirected to the URL after SSO succeeds. If you do not configure this parameter, users are redirected to the homepage of the Alibaba Cloud Management Console after SSO succeeds.

            **Note:** For security purposes, you must enter a URL that points to an Alibaba website for the `RelayState` parameter. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com.


After you configure Alibaba Cloud as a trusted SAML SP, you must configure SAML assertions for your IdP. For more information, see [SAML response for user-based SSO](/intl.en-US/SSO Management/User-based SSO/SAML response for user-based SSO.md).

