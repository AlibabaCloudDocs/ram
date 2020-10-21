# Implement user-based SSO from Azure AD

This topic provides an example of how to implement user-based single sign-on \(SSO\) to Alibaba Cloud from Azure Active Directory \(Azure AD\). This topic also describes the end-to-end identity SSO process from an identity provider \(IdP\) to Alibaba Cloud.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An Azure AD account is created.

## Download the SAML SP metadata file of Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **User-based SSO** tab, click **Copy** next to **SAML Service Provider Metadata URL**.

4.  On a new page, paste the URL in the address bar to download the metadata file in the XML format.

    **Note:** The XML file contains the information that is required to configure Alibaba Cloud as a SAML service provider \(SP\). Save the values of the `entityID` and `Location` attributes for subsequent use.


## Create an application in Azure AD

1.  Log on to the[Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  On the page that appears, click **New application**.

    ![New application](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4320549951/p43721.png)

5.  On the **Add an application** page, click **Non-gallery application**.

6.  On the **Add your own application** page, enter an application name and click **Add**.

    **Note:** In this example, the application name is AliyunSSODemo.


## Configure SAML in Azure AD

1.  Click AliyunSSODemo.

2.  On the **Overview** page, click **Single sign-on**.

    ![Single sign-on](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p43729.png)

3.  On the Select a single sign-on method page, click **SAML**.

    ![SAML](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/3726498951/p43727.png)

4.  On the **Set up Single Sign-On with SAML** page, perform the following steps:

    1.  In the upper-left corner, click **Upload metadata file**, select a file, and then click **Add**.

        ![Upload a metadata file](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p43731.png)

        **Note:** In this example, the XML file that you downloaded in [Download the SAML SP metadata file of Alibaba Cloud](#section_1mf_pid_z9k) is uploaded.

    2.  In the **Basic SAML Configuration** section, click the ![Edit](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p112341.png) icon in the upper-right corner.

    3.  In the **Basic SAML Configuration** pane, enter the value of `entityID` in the **Identifier \(Entity ID\) field**, enter the value of `Location` in the **Reply URL \(Assertion Consumer Service URL\)** field, enter https://ram.console.aliyun.com in the **Relay State** field, and then click **Save**. You can obtain the values of the entityID and Location attributes from the metadata file of Alibaba Cloud.

    4.  In the **SAML Signing Certificate** section, click **Download** to the right of **Federation Metadata XML**.

        ![Download the federation metadata XML file](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p44054.png)


## Create a RAM user in Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account.

2.  Create a RAM user named username@\{id\}.onaliyun.com.

    **Note:**

    -   The username must be the same as the prefix of the Azure AD username. In this example, the username is u2.
    -   For information about how to create a RAM user, see [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

## Enable user-based SSO in Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  Click the **User-based SSO** tab.

4.  Click **Modify** next to **SSO Settings**.

5.  In the SSO Settings pane, select **Enabled** under **SSO Status**.

    **Note:** User-based SSO is a global feature. If you select Enabled for SSO Status, user-based SSO is enabled for all RAM users. This means that all RAM users can log on to the Alibaba Cloud Management Console only by using SSO. If you are using a RAM user, select Disabled for SSO Status in this step. Before you enable user-based SSO, you must complete the SSO settings for the RAM user. Otherwise, logon by using the RAM user fails. To avoid this issue, you can use the Alibaba Cloud account to configure user-based SSO.

6.  Click **Upload** under **Metadata File** to upload the XML file that you obtained in [Configure SAML in Azure AD](#section_755_ua6_j4m).

7.  Turn on **Auxiliary Domain**. In the field that appears, enter u2.onmicrosoft.com.

8.  Click **OK**.


## Create and assign a user in Azure AD

1.  Log on to the[Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  In the **Name** column, click **AliyunSSODemo**.

5.  In the left-side navigation pane, click **Users and groups**.

6.  In the upper-left corner, click **Add user**.

    ![Add a user](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p44178.png)

7.  On the Add Assignment page, click **Users**. In the Users pane, select u2 and click **Select**.

    ![Select a user](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5320549951/p44179.png)

8.  Click **Assign**.


## Test role-based SSO

1.  Log on to the[Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  In the **Name** column, click **AliyunSSODemo**.

5.  On the **Overview** page, click **Single sign-on**.

6.  On the **Set up Single Sign-On with SAML** page, click **Test**.

    ![test](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5320549951/p113621.png)

7.  In the Test single sign-on with AliyunSSODemo pane, click **Sign in as current user**.

    ![Sign in as the current user](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7420549951/p44191.png)


If the page shown in the following figure appears, user-based SSO is successful.

![SSO_Okta configuration verification](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5320549951/p111769.png)

