# Implement user-based SSO by using Azure AD

This topic provides an example of how to implement user-based single sign-on \(SSO\) between Alibaba Cloud and Azure Active Directory \(Azure AD\). This topic also describes how to implement end-to-end identity SSO between an identity provider \(IdP\) and Alibaba Cloud.

Before you start, you must create an Alibaba Cloud account and an Azure AD tenant. An administrator and an organization user \(u2\) are added to the Azure AD tenant. The administrator is assigned the global administrator permissions You want the organization user \(u2\) to access Alibaba Cloud as a Resource Access Management \(RAM\) user.

You must log on to the Azure portal as an Azure AD Global administrator and perform the following steps in this example. For more information about how to create and authorize users in Azure AD, see the [Azure AD documentation](https://docs.microsoft.com/zh-cn/azure/active-directory/fundamentals).

## Step 1: Download the SAML SP metadata file of Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **User-based SSO** tab, click **Copy** next to **SAML Service Provider Metadata URL**.

4.  On a new page, paste the URL in the address bar to download the metadata file in the XML format.

    **Note:** The XML file contains the information that is required to configure Alibaba Cloud as a SAML service provider \(SP\). Save the values of the `entityID` and `Location` attributes for subsequent use.


## Step 2: Create an application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner of the page, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  On the page that appears, click **New application**.

5.  On the **Browse Azure AD Gallery \(Preview\)** page, click **Create your own application**.

6.  In the **Create your own application** pane, enter a name for your application, for example, AliyunSSODemo. Then, select **Integrate any other application you don't find in the gallery** and click **Create**.


## Step 3: Configure SAML in Azure AD

1.  On the **AliyunSSODemo** page, click **Single sign-on** in the left-side navigation pane.

2.  On the Select a single sign-on method page, click **SAML**.

3.  On the **Set up Single Sign-On with SAML** page, perform the following steps:

    1.  In the upper-left corner of the page, click **Upload metadata file**, select a file, and then click **Add**.

        ![Upload the metadata file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3754139061/p187566.png)

        **Note:** In this example, the XML file that you downloaded in [Step 1: Download the SAML SP metadata file of Alibaba Cloud](#section_1mf_pid_z9k) is uploaded.

    2.  In the **Basic SAML Configuration** pane, set the following parameters and click **Save**.

        -   **Identifier \(Entity ID\)**: By default, this parameter is set to the value of the `entityID` parameter that is read from the preceding metadata file.
        -   **Reply URL \(Assertion Consumer Service URL\)**: By default, this parameter is set to the value of the `Location` parameter that is read from the preceding metadata file.
        -   **Relay State**: Enter the URL of the Alibaba Cloud service page to which an Azure AD user is redirected after the user logs on to Azure AD through SSO.

            **Note:** To ensure high security, you must enter a URL that points to a website of Alibaba Group in the **Relay State** field. For example, you can enter one of the following domain names in the Relay State field: \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this field is left empty, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to Azure AD.

    3.  In the **SAML Signing Certificate** section, click **Download** in the **Federation Metadata XML** field to download the related XML file.

        ![Download the related federation metadata XML file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3660957061/p44054.png)


## Step 4: Assign a user to the application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner of the homepage, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  In the **Name** column, click **AliyunSSODemo**.

5.  In the left-side navigation pane, click **Users and groups**.

6.  In the upper-left corner of the page, click **Add user**.

    ![Add a user](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44178.png)

7.  On the Add Assignment page, click **Users**. In the Users pane, select u2 and click **Select**.

    ![Select a user](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5320549951/p44179.png)

8.  Click **Assign**.


## Step 5: Create a RAM user in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  Create a RAM user named <username\>@<AccountAlias\>.onaliyun.com.

    **Note:**

    -   <username\> indicates the username of the RAM user. <AccountAlias\>.onaliyun.com indicates the default domain name. The username must be the same as the prefix of the Azure AD username. The username is u2 in this example.
    -   For more information about how to create a RAM user, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

## Step 6: Enable user-based SSO in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  Click the **User-based SSO** tab.

4.  Click **Modify** next to **SSO Settings**.

5.  In the SSO Settings pane, select **Enabled** in the **SSO Status** field.

    **Note:** User-based SSO takes effect on a global scale. After this feature is enabled, all RAM users must log on to the Alibaba Cloud Management Console through SSO. If you are using a RAM user, set the SSO Status parameter to Disabled in this step. You must complete the SSO settings for the RAM user before you enable user-based SSO. Otherwise, logon based on the RAM user will fail. To avoid this issue, you can also use the Alibaba Cloud account to configure user-based SSO.

6.  In the **Metadata File** field, click **Upload** to upload the XML file that you obtained in [Step 3: Configure SAML in Azure AD](#section_755_ua6_j4m).

7.  Turn on the **Auxiliary Domain** switch. In the field that appears, enter the domain name of the email address that you use as the Azure AD username.

    In this example, the domain name is test.onmicrosoft.com because the username of the Azure AD user \(u2\) is u2@test.onmicrosoft.com.

8.  Click **OK**.


## Verify the user-based SSO configurations

-   Log on from the Alibaba Cloud Management Console
    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account. On the **Overview** page, copy the logon URL of a RAM user.
    2.  Move the pointer over the profile picture in the upper-right corner of the page, and click **Log out**. Then, paste the logon URL into the address bar of a browser. You can also access the URL in a new page.
    3.  On the page that appears, click **Logon with Organization Account**. You are redirected to the logon page of Azure AD.

        ![Log on by using an organization account](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4754139061/p185807.png)

    4.  Log on by using u2.

        You are redirected to the page that is specified by the **Relay State** parameter. If the **Relay State** parameter is invalid or not specified, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to Azure AD.

        ![Verify the user-based SSO configurations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)

-   Log on from Azure AD
    1.  Obtain the user access URL.
        1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.
        2.  In the upper-left corner of the page, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.
        3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
        4.  Click **AliyunSSODemo**.
        5.  In the left-side navigation pane, click **Properties** and obtain the **user access URL**.

            You can enter the **user access URL** in the address bar of your browser to access the application AliyunSSODemo.

            ![User access URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4754139061/p187940.png)

    2.  After you obtain the **user access URL**, enter the URL in the address bar of a browser, and log on by using u2.

        You are redirected to the page that is specified by the **Relay State** parameter. If the **Relay State** parameter is invalid or not specified, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on.

        ![Verify the user-based SSO configurations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)


