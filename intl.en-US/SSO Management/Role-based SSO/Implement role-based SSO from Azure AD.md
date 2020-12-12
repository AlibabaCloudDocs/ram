# Implement role-based SSO from Azure AD

This topic provides an example on how to implement role-based single sign-on \(SSO\) from Azure Active Directory \(Azure AD\) to Alibaba Cloud. This topic describes the end-to-end identity SSO process from an identity provider \(IdP\) to Alibaba Cloud.

In this example, you have an Alibaba Cloud account \(Account1\) and an Azure AD user \(u2\). You want to use Azure AD to manage your users and configure enterprise applications such as Alibaba Cloud services. After you configure role-based SSO, you can better manage your Azure AD users who have access to Alibaba Cloud and manage your accounts in the Azure portal. The AD users can log on to the Alibaba Cloud Management Console with their Azure AD accounts.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p44059.png)

## Step 1: Create an application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  On the page that appears, click **New application**.

5.  In the **Add from the gallery** section of the Add an application page, enter **Alibaba Cloud Service \(Role-based SSO\)** in the field and press Enter. Then, select Alibaba Cloud Service \(Role-based SSO\).

6.  On the page that appears, click **Add**.

7.  On the Alibaba Cloud Service \(Role-based SSO\) page, click **Properties** in the left-side navigation pane and copy and save the **object ID** for subsequent use.

    ![Object ID](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p43726.png)


## Step 2: Configure SSO in Azure AD

1.  In the left-side navigation pane of the Alibaba Cloud Service \(Role-based SSO\) page, click **Single sign-on**.

    ![Single sign-on](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p43729.png)

2.  In the Select a single sign-on method section, click **SAML**.

3.  On the Set up Single Sign-On with SAML page, perform the following steps:

    1.  In the upper-left corner, click **Upload metadata file**, select a file, and then click **Add**.

        ![Upload a metadata file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p43731.png)

        **Note:** You can obtain the metadata file from the URL `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

    2.  In the **User Attributes & Claims** section, click the ![Edit icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p112341.png) icon.

    3.  Click **Add new claim**, configure the parameters, and then click **Save**.

        -   Enter `Role` in the **Name** field.
        -   Enter `https://www.aliyun.com/SAML-Role/Attributes` in the **Namespace** field.
        -   Select **Attribute** from the **Source** drop-down list.
        -   Select `user.assignedroles` from the **Source attribute** drop-down list.
    4.  Repeat the preceding step to add another claim and configure the parameters.

        -   Enter `RoleSessionName` in the **Name** field.
        -   Enter `https://www.aliyun.com/SAML-Role/Attributes` in the **Namespace** field.
        -   Select **Attribute** from the **Source** drop-down list.
        -   Select `user.userprincipalname` from the **Source attribute** drop-down list.
    5.  In the upper-right corner of the User Attributes & Claims page, click the Close icon. In the **SAML Signing Certificate** section, click **Download** next to **Federation Metadata XML** to download the federation metadata XML file for subsequent use.

        ![Download the federation metadata XML file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3660957061/p44054.png)

    6.  In the **Set up Alibaba Cloud Service \(Role-based SSO\)** section, copy and save the logon URL**xxx**, Azure AD identifier**xxx**, and logout URL**xxx** for subsequent use.


## Step 3: Create an IdP in Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using Account1.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** page, click **Create IdP**.

4.  On the page that appears, set **IdP Name** to `AAD` and set **Note** based on your requirements.

5.  Click **Upload** under **Metadata File** to upload the federation metadata XML file that you downloaded earlier.

    **Note:** You must upload the federation metadata XML file**xxx** that you downloaded in [Step 2: Configure SSO in Azure AD](#section_hcw_ey6_57b).

6.  Click **OK**.


## Step 4: Create a RAM role in Alibaba Cloud

1.  After the IdP is created, click **Create RAM Role**.

2.  On the page that appears, click **Create RAM Role**.

3.  In the Create RAM Role panel, set Trusted entity type to **IdP** and click **Next**.

4.  Set **RAM Role Name** to `AADrole` and set **Note** based on your requirements.

5.  Select `AAD` from the Select IdP drop-down list and click **OK**.

    **Note:**

    -   You can grant permissions to the role based on your business requirements. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).
    -   After you create the IdP and the RAM role, save the Alibaba Cloud Resource Names \(ARNs\) of the IdP and the RAM role for subsequent use. For more information about how to obtain the ARN of the RAM role, see [View the basic information of a RAM role](/intl.en-US/RAM Role Management/View the basic information of a RAM role.md).
6.  Click **Close**.


## Step 5: Associate the Alibaba Cloud RAM role with the Azure AD user

1.  Create a role in Azure AD.

    1.  Log on to the [Azure AD Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer) by using u2.

    2.  Click the ![settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8707577061/p139775.png) icon next to the account.

    3.  Click **Select permissions**.

    4.  In the Permissions panel, select the following permissions and click **Consent**.

        ![Permissions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44135.png)

        **Note:** After the permissions are granted, you are redirected to Graph Explorer.

    5.  On the Graph Explorer page, select **GET** from the first drop-down list and select **beta** from the second drop-down list. Then, enter `https://graph.microsoft.com/beta/servicePrincipals` in the field next to the drop-down lists, and click **Run Query**.

        **Note:** If you have multiple directories, enter `https://graph.microsoft.com/beta/contoso.com/servicePrincipals` in the field next to the drop-down lists.

    6.  On the **Response Preview** tab, copy the `appRoles` property from the `Service Principal` object for subsequent use.

        ```
         "appRoles": [
                        {
                            "allowedMemberTypes": [
                                "User"
                            ],
                            "description": "msiam_access",
                            "displayName": "msiam_access",
                            "id": "7dfd756e-8c27-4472-b2b7-38c17fc5****",
                            "isEnabled": true,
                            "origin": "Application",
                            "value": null
                        }
                    ],
        ```

        **Note:** To find the `appRoles` property, enter `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` in the field next to the drop-down lists. Note that the `objectID` variable indicates the object ID that you copied from the Properties page of the Azure portal.**xxx**

    7.  Go back to **Graph Explorer**, select **PATCH** from the first drop-down list and select **beta** from the second drop-down list. Enter `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` in the text box next to the drop-down lists. Copy and paste the following sample script into the **Request Body** section, edit the script based on your business requirements, and click **Run Query**.

        ```
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "41be2db8-48d9-4277-8e86-f6d22d35****",
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078c****",
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD"// The ARNs of the IdP and the RAM role.
            }
          ]
        }
        ```

        **Note:** You can create multiple roles based on your business requirements. Azure AD will send the ARNs of these roles and their IdPs as the claim value in a SAML response. However, you can add new roles only after the `msiam_access` part of the patch operation.

2.  Perform the following steps to associate the RAM role with the Azure AD user u2:

    1.  Log on to the **Azure portal** as an administrator.

    2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

    3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.

    4.  In the left-side navigation pane, click **Users and groups**.

    5.  In the upper-left corner, click **Add user**.

        ![Add a user](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44178.png)

    6.  On the page that appears, click **Users**, select u2 from the user list, and then click **Select**.

    7.  Click **Assign**.

    8.  View the assigned role.

        ![View the assigned role](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44185.png)

        **Note:** After you assign the RAM role to the user u2, the role is automatically attached to the user. If you have created multiple RAM roles, you must attach an appropriate role to the user. If you want to implement role-based SSO from Azure AD to multiple Alibaba Cloud accounts, repeat the preceding steps.


## Test user-based SSO

1.  Log on to the **Azure portal** as an administrator.

2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.

4.  In the left-side navigation pane, click **Single sign-on**.

5.  In the **Validate single sign-on with Alibaba Cloud Service \(Role-based SSO\)** section, click **Validate**.

    ![Validate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44188.png)

    **Note:** Before you use u2 to test role-based SSO, make sure that u2 is added to a group in Azure AD.

6.  Click **Sign in as current user**.

    ![Sign in as the current user](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44191.png)

7.  On the page for selecting a logon accountxxx, select u2.


If the following page appears, role-based SSO is successful.

![Successful role-based SSO](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44194.png)

