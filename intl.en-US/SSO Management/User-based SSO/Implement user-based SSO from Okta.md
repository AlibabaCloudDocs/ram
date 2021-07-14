# Implement user-based SSO from Okta

This topic provides an example on how to implement user-based single sign-on \(SSO\) from Okta to Alibaba Cloud. This topic also describes the end-to-end SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud.

An Okta account is created.

**Note:** A 30-day free trial is available for each Okta account.

## Step 1: Download the SAML SP metadata file of Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the SSO page, click the **User-based SSO** tab.

4.  In the **SSO Settings** section, copy the value of **SAML Service Provider Metadata URL**.

5.  Open a new tab in your browser, paste the URL in the address bar, and then download the SAML service provider \(SP\) metadata file in the XML format.

    **Note:** The XML file contains the information that is required to configure Alibaba Cloud as a SAML SP. Record the value of `entityID` in the `EntityDescriptor` element and the value of `Location` in the `AssertionConsumerService` element for subsequent use.


## Step 2: Create an application that supports SAML 2.0-based SSO in Okta

1.  Log on to the [Okta portal](https://www.okta.com/).

    **Note:** A dynamic 6-digit verification code is required for the logon. The verification code is provided by the Okta Verify app. Therefore, you must install the Okta Verify app on your mobile phone before the logon.

2.  In the upper-right corner of the Okta portal, click the account name and select **Your Org** from the drop-down list.

3.  In the upper-right corner, click **Admin**.

    ![SSO_Okta_Admin](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9690549951/p111967.png)

4.  In the top navigation bar, click **Applications**.

    ![SSO_Okta_Applications](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9690549951/p111964.png)

5.  On the page that appears, click **Add Application**.

6.  On the page that appears, click **Create New App**.

7.  In the dialog box that appears, select **Web** for the **Platform** parameter, select **SAML 2.0** for the **Sign on method** parameter, and then click **Create**.

8.  Enter AliyunSSODemo in the App name field and click **Next**.

9.  Configure the parameters and click **Next**.

    ![Configure SAML](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9111322061/p139878.png)

    -   In the **Single sign on URL** field, enter the value of `Location` that you obtained in [Step 1: Download the SAML SP metadata file of Alibaba Cloud](#section_7q5_glq_tbn).
    -   In the **Audience URI** field, enter the value of `entityID` that you obtained in [Step 1: Download the SAML SP metadata file of Alibaba Cloud](#section_7q5_glq_tbn).
    -   In the **Default RelayState** field, enter a URL. Then, the system redirects you to the URL after logon.

        **Note:** For security purposes, you must enter a URL that points to an Alibaba website in the **Default RelayState** field. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this field is empty, you are redirected to the homepage of the Alibaba Cloud Management Console after logon.

    -   Select **Persistent** for **Name ID format**.
    -   Select **Email** for **Application username**.
10. Select an application type based on your business requirements and click **Finish**.


## Step 3: Download the SAML IdP metadata file of Okta

1.  In the top navigation bar, click **Applications**.

2.  Click the application name AliyunSSODemo.

3.  On the **Sign On** tab, click **Identity Provider metadata** to download the metadata file.

    ![SSO_Okta_Sign On](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0790549951/p111987.png)


## Step 4: Enable user-based SSO in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the SSO page, click the **User-based SSO** tab.

4.  Click **Modify** to the right of **SSO Settings**.

5.  In the **SSO Status** section of the SSO Settings panel, click **Enabled**.

    **Note:** User-based SSO takes effect on all RAM users in your Alibaba Cloud account. If you enable this feature, all RAM users in your Alibaba Cloud account must log on to the Alibaba Cloud Management Console by using SSO. If you use a RAM user, set the SSO Status parameter to Disabled in this step. Before you enable user-based SSO, you must complete the SSO settings for the RAM user. Otherwise, you cannot log on as the RAM user. To avoid this issue, you can also use the Alibaba Cloud account to configure user-based SSO.

6.  In the **Metadata File** section, click **Upload** to upload the IdP metadata file obtained from [Step 3: Download the SAML IdP metadata file of Okta](#section_gja_2u2_so7).

7.  Select **Enabled** for **Auxiliary Domain**. In the field that appears, enter the domain name of the email address that you use as the Okta username.

    **Note:** If usernames that belong to your Okta account are suffixed with different domain names, only the users whose usernames are suffixed with the specified domain name can log on to the Alibaba Cloud Management Console.

8.  Click **OK**.


## Step 5: Create a user and assign the application to the user in Okta

1.  In the top navigation bar, choose **Directory** \> **People**.

    ![OSS_Okta_poeple](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1790549951/p113589.png)

2.  On the page that appears, click **Add Person**. In the **Add Person** dialog box, enter u2@examplecompany.com in the **Primary email** field and configure other parameters.

3.  Set **Password** to **Send user activation email now** and click **Save**.

    **Note:** Follow the instructions to activate the Okta user.

4.  In the top navigation bar, click **Applications**.

5.  Click the application name AliyunSSODemo. On the **Assignments** tab, choose **Assign** \> **Assign to People**.

6.  In the dialog box that appears, click **Assign** to the right of the u2@examplecompany.com user.

7.  Click **Save and Go Back**.

8.  Click **Done**.


## Step 6: Create a RAM user in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, choose **Identities** \> **Users**.

3.  On the Users page, click **Create User**.

4.  On the Create User page, specify the **Logon Name** and **Display Name** parameters.

    **Note:** The logon name and Okta username must have the same prefix. In this example, the prefix of the logon name must be u2.

5.  In the **Access Mode** section, select **Console Password Logon** and configure the parameters.

6.  Click **OK**.


## Verify the user-based SSO configurations

-   Logon from Alibaba Cloud

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account. On the **Overview** page, copy the logon URL of a RAM user.
    2.  Move the pointer over the profile picture in the upper-right corner of the page, and click **Log Out**. Then, paste the logon URL into the address bar of a browser. You can also access the URL on a new tab.
    3.  On the page that appears, click **Logon with Organization Account**. The system redirects you to the logon page of Okta.

        ![Log on by using an organization account](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4754139061/p185807.png)

    4.  On the logon page of Okta, enter the username u2@examplecompany.com and password, and click **Login**.
    After the logon succeeds, you are redirected to the page that is specified by **DefaultRelayState**. If **DefaultRelayState** is not configured or invalid, you are redirected to the homepage of the Alibaba Cloud Management Console. If the page shown in the following figure appears, the user-based SSO configuration is successful.

    ![SSO_Okta configuration verification](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)

-   Logon from Okta

    Log on to the [Okta portal](https://www.okta.com/) as an Okta user. On the page that appears, click the **AliyunSSODemo** application.

    After the logon succeeds, you are redirected to the page that is specified by **DefaultRelayState**. If **DefaultRelayState** is not configured or invalid, you are redirected to the homepage of the Alibaba Cloud Management Console. If the page shown in the following figure appears, the user-based SSO configuration is successful.

    ![SSO_Okta configuration verification](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)


