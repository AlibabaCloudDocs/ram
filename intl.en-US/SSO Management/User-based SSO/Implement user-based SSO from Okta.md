# Implement user-based SSO from Okta

This topic provides an example of how to implement user-based single sign-on \(SSO\) from Okta to Alibaba Cloud. It describes the end-to-end SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An Okta account is created.

    **Note:** A 30-day free trial is available for each Okta account.


## Step 1: Download the SAML SP metadata file of Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with the Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **User-based SSO** tab, click **Copy** next to **SAML Service Provider Metadata URL**.

4.  On a new page, paste the URL in the address bar to download the SAML service provider \(SP\) metadata file in the XML format.

    **Note:** The XML file contains the information that is required to configure Alibaba Cloud as an SAML SP. Save the value of `entityID` in the `EntityDescriptor` element and the value of `Location` in the `AssertionConsumerService` element for subsequent use.


## Step 2: Create an application in Okta

1.  Log on to the [Okta portal](https://www.okta.com/).

    **Note:** A dynamic 6-digit verification code is required for the logon. The verification code is provided by the Okta Verify app. Therefore, you must install the Okta Verify app on your smart phone before the logon.

2.  In the upper-right corner of the Okta portal, click the account name, and select **Your Org** from the drop-down menu.

3.  In the upper-right corner, click **Admin**.

    ![SSO_Okta_Admin](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9690549951/p111967.png)

4.  In the top navigation bar, click **Applications**.

    ![SSO_Okta_Applications](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/9690549951/p111964.png)

5.  On the **Applications** page, click **Add Application**.

6.  On the **Add Application** page, click **Create New App**.

7.  In the **Create a New Application Integration** dialog box, select **Web** from the **Platform** drop-down list, select **SAML 2.0** as **Sign on method**, and then click **Create**.

8.  In the **General Settings** step, enter AliyunSSODemo in the **App name** field and click **Next**.

9.  In the **Configure SAML** step, set the parameters and click **Next**.

    ![Configure SAML ](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2320549951/p139878.png)

    -   In the **Single sign on URL** field, enter the value of `entityID` that you obtained in [Step 1: Download the SAML SP metadata file of Alibaba Cloud](#section_7q5_glq_tbn).
    -   In the **Audience URI** field, enter the value of `Location` that you obtained in [Step 1: Download the SAML SP metadata file of Alibaba Cloud](#section_7q5_glq_tbn).
    -   Enter a URL in the **Default RelayState** field. A user is redirected to the URL after logon.

        **Note:** For security purposes, you must specify a URL that points to an Alibaba website. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If the URL that you specify does not point to an Alibaba website, the setting is invalid. If this field is left empty, a user is redirected to the homepage of the Alibaba Cloud Management Console by default after logon.

    -   Select **Persistent** from the **Name ID format** drop-down list.
    -   Select **Email** from the **Application username** drop-down list.
10. Select an application type based on your business requirements and click **Finish**.


## Step 3: Download the SAML IdP metadata file of Okta

1.  In the top navigation bar, click **Applications**.

2.  Click the application name \(AliyunSSODemo\).

3.  On the **Sign On** tab, click **Identity Provider metadata** to download the SAML IdP metadata file.

    ![SSO_Okta_Sign On](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/0790549951/p111987.png)


## Step 4: Enable user-based SSO in Alibaba Cloud

1.  In the left-side navigation pane of the RAM console, click **SSO**.

2.  Click the **User-based SSO** tab.

3.  Click **Modify** next to **SSO Settings**.

4.  In the **SSO Settings** pane, select **Enabled** under **SSO Status**.

    **Note:** User-based SSO is a global feature. If you select **Enabled** under **SSO Status**, user-based SSO is enabled for all RAM users. This means that all RAM users can log on to the Alibaba Cloud Management Console only by using SSO. If you are using a RAM user, select **Disabled** under **SSO Status** in this step. You must complete the SSO settings for the RAM user before you enable user-based SSO. Otherwise, logon based on the RAM user will fail. To avoid this issue, you can use the Alibaba Cloud account to configure user-based SSO.

5.  Click **Upload** under **Metadata File** to upload the SAML IdP metadata file that you downloaded in [Step 3: Download the SAML IdP metadata file of Okta](#section_gja_2u2_so7).

6.  Turn on the **Auxiliary Domain** switch. In the field that appears, enter the domain name of the email address that you use as the Okta username.

    **Note:** If usernames under your Okta account are suffixed with different domain names, only the users whose usernames are suffixed with the specified domain name can log on to the Alibaba Cloud Management Console.

7.  Click **OK**.


## Step 5: Add a user and assign the application to the user in Okta

1.  In the top navigation bar of the Okta portal, choose **Directory** \> **People**.

    ![OSS_Okta_poeple](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1790549951/p113589.png)

2.  On the **People** page, click **Add People**. In the **Add Person** dialog box, enter test@example.com in the **Primary email** field and set other parameters.

3.  Select the **Send user activation email now** check box under the **Password** field and click **Save**.

    **Note:** Activate the Okta user as prompted.

4.  In the top navigation bar, click **Applications**.

5.  Click the application name \(AliyunSSODemo\). On the **Assignments** tab, choose **Assign** \> **Assign to People**.

6.  In the dialog box that appears, click **Assign** next to the test@example.com user.

7.  Click **Save and Go Back**.

8.  Click **Done**.


## Step 6: Create a RAM user in Alibaba Cloud

1.  In the left-side navigation pane of the RAM console, choose **Identities** \> **Users**.

2.  On the **Users** page, click **Create User**.

3.  On the **Create User** page, set the **Logon Name** and **Display Name** parameters.

    **Note:** The prefix of the logon name must be the same as the prefix of the Okta username.

4.  In the **Access Mode** section, select **Console Password Logon** and set the parameters that are related to the parameter and multi-factor authentication \(MFA\).

5.  Click **OK**.


## Test user-based SSO

-   Logon from Alibaba Cloud

    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with the Alibaba Cloud account. On the **Overview** page, copy the logon URL of RAM users.
    2.  Move the pointer over the profile picture in the upper-right corner, and select **Sign out** from the shortcut menu. Paste the copied logon URL in the address bar. Alternatively, paste the URL in the address bar of a new page.
    3.  On the page that appears, click **Logon with Organization Account**. You are redirected to the logon page of Okta.
    4.  On the logon page of Okta, enter the username \(test@example.com\) and password, and then click **Sign In**.
    You are redirected to the page that is specified by the **Default RelayState** parameter. If the **Default RelayState** parameter is invalid or left empty, you are redirected to the homepage of the Alibaba Cloud Management Console. If the page shown in the following figure appears, it indicates that user-based SSO is successful.

    ![SSO_test](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5320549951/p111769.png)

-   Logon from Okta

    Log on to the [Okta portal](https://www.okta.com/) as an Okta user. On the page that appears, click the **AliyunSSODemo** application.

    After the logon to the Alibaba Cloud console is successful, you are redirected to the page that is specified by the **Default RelayState** parameter. If the **Default RelayState** parameter is invalid or left empty, you are redirected to the homepage of the Alibaba Cloud Management Console. If the page shown in the following figure appears, it indicates that user-based SSO is successful.

    ![SSO_test](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5320549951/p111769.png)


