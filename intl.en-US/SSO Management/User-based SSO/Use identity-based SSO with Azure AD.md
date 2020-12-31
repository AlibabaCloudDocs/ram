# Use identity-based SSO with Azure AD

This topic provides an example on how to use identity-based single sign-on \(SSO\) to access Alibaba Cloud from Azure Active Directory \(Azure AD\). The example includes steps that are required to configure SSO on both the identity provider \(IdP\) and Alibaba Cloud ends.

Before you start, you must create an Alibaba Cloud account and an Azure AD tenant. An administrator and an organization user \(u2\) are added to the Azure AD tenant. The administrator is assigned the global administrator permissions. You want the organization user \(u2\) to access Alibaba Cloud as a Resource Access Management \(RAM\) user.

To complete the configuration in Azure AD, you must log on to the Azure portal as the administrator that is granted the global administrator permissions. For more information about how to create and authorize users in Azure AD, see [Azure AD documentation](https://docs.microsoft.com/zh-cn/azure/active-directory/fundamentals).

## Step 1: Download the SAML SP metadata file from Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with your Alibaba Cloud account.

2.  In the left-side navigation pane of the homepage, click **SSO**.

3.  On the **User-based SSO** tab, click **Copy** next to **SAML Service Provider Metadata URL**.

4.  Open a new page in your browser and paste the URL in the address bar to download the metadata file in XML format.

    **Note:** The XML file contains information about Alibaba Cloud serving as a SAML service provider \(SP\). Save the values of the `entityID` and `Location` attributes for subsequent use.


## Step 2: Create an application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as the administrator.

2.  In the upper-left corner of the homepage, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  On the page that appears, click **New application**.

5.  On the **Browse Azure AD Gallery \(Preview\)** page, click **Create your own application**.

6.  In the **Create your own application** pane, enter a name for your application. AliyunSSODemo is entered in this example. Then, select **Integrate any other application you don't find in the gallery** and click **Create**.


## Step 3: Configure SAML in Azure AD

1.  On the **AliyunSSODemo** page, click **Single sign-on** in the left-side navigation pane.

2.  On the Select a single sign-on method page, click **SAML**.

3.  On the **Set up Single Sign-On with SAML** page, perform the following steps:

    1.  In the upper-left corner of the page, click **Upload metadata file**, select a file, and then click **Add**.

        ![Upload the metadata file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3754139061/p187566.png)

        **Note:** In this example, the XML file that you downloaded in [Step 1: Download the SAML SP metadata file from Alibaba Cloud](#section_1mf_pid_z9k) is uploaded.

    2.  In the **Basic SAML Configuration** pane, set the following parameters and click **Save**:

        -   **Identifier \(Entity ID\)**: By default, the value is automatically set to the value of `entityID` that is read from the preceding metadata file.
        -   **Reply URL \(Assertion Consumer Service URL\)**: By default, the parameter is automatically set to the value of `Location` that is read from the preceding metadata file.
        -   **Relay State**: Enter the URL of the Alibaba Cloud service page to which an Azure AD user is redirected after the user successfully logs on through SSO.

            **Note:** For security purposes, you must enter a URL that points to a website of Alibaba Group in the **Relay State** field. For example, the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this field is left empty, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to Azure AD.

    3.  In the **SAML Signing Certificate** section, perform the following steps to query **Federation Metadata XML**.

        1.  Click **New Certificate**.
        2.  Add a new certificate and click **Save**.
        3.  Reload the page and click **Download** next to **Federation Metadata XML** to download the metadata file.

            ![Download the federation metadata XML file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3660957061/p44054.png)


## Step 4: Assign a user to the application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as the administrator.

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

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with your Alibaba Cloud account.

2.  Create a RAM user named <username\>@<AccountAlias\>.onaliyun.com.

    **Note:**

    -   <username\> indicates the username of the RAM user. <AccountAlias\>.onaliyun.com indicates the default domain name. The username must be the same as the prefix of the Azure AD username. The username is u2 in this example.
    -   For more information about how to create a RAM user, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

## Step 6: Enable identity-based SSO in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  Click the **User-based SSO** tab.

4.  Click **Modify** next to **SSO Settings**.

5.  In the SSO Settings pane, select **Enabled** under **SSO Status**.

    **Note:** Identity-based SSO takes effect on a global scale. After this feature is enabled, all RAM users must log on to the Alibaba Cloud Management Console through SSO. If your account is a RAM user, select Disabled for SSO Status in this step and complete the SSO settings before you enable identity-based SSO. This prevents logon failures in case of you making any user errors when you configure the SSO settings. To avoid this issue, you can also use an Alibaba Cloud account to configure identity-based SSO.

6.  Click **Upload** under **Metadata File** to upload the XML file that you obtained in [Step 3: Configure SAML in Azure AD](#section_755_ua6_j4m).

7.  Turn on **Auxiliary Domain**. In the field that appears, enter the domain name of the email address that you use as the Azure AD username.

    In this example, the domain name is test.onmicrosoft.com because the username of the Azure AD user \(u2\) is u2@test.onmicrosoft.com.

8.  Click **OK**.


## Verify the identity-based SSO configurations

-   Log on from the Alibaba Cloud Management Console
    1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with the Alibaba Cloud account. On the **Overview** page, copy the logon URL that is assigned to RAM users.
    2.  Move the pointer over the profile picture in the upper-right corner, and click **Log Out** and enter the copied logon URL into the address bar. You can also access the URL in a new page.
    3.  On the page that appears, click **Login with Organization Account**. The system redirects you to the logon page of Azure AD.

        ![Log on with an organization account](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4754139061/p185807.png)

    4.  Log on with the Azure AD user \(u2\).

        You are redirected to the page that is specified by **Relay State**. If the value of **Relay State** is not specified or invalid, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to Azure AD.

        ![Verify the identity-based SSO configurations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)

-   Log on from Azure AD
    1.  Obtain the user access URL.
        1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as the administrator.
        2.  In the upper-left corner of the page, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.
        3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.
        4.  Click **AliyunSSODemo**.
        5.  In the left-side navigation pane, click **Properties** and find the **user access URL**.

            You can enter the **user access URL** in your browser to access the application AliyunSSODemo.

            ![User access URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4754139061/p187940.png)

    2.  After you obtain the **user access URL**, enter the URL in the browser, and then log on with account u2.

        You are redirected to the page that is specified by **Relay State**. If the value of **Relay State** is not specified or invalid, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on.

        ![Verify the identity-based SSO configurations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1676577061/p111769.png)


