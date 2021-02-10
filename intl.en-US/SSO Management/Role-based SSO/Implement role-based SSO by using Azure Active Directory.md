# Implement role-based SSO by using Azure Active Directory

This topic provides an example of how to implement role-based single sign-on \(SSO\) between Azure Active Directory \(Azure AD\) and Alibaba Cloud. This topic also describes how to implement end-to-end identity SSO between an identity provider \(IdP\) and Alibaba Cloud.

In this example, you have an Alibaba Cloud account \(Account1\) and an Azure AD user \(u2\). An administrator and an organization user \(u2\) are added to the Azure AD tenant. The administrator is assigned the global administrator permissions. You want the organization user \(u2\) to access Alibaba Cloud with Account1 by using role-based SSO.

To complete the configuration in Azure AD, you must log on to the Azure portal as an administrator. In this case, make sure that the administrator is granted the global administrator permissions. For more information about how to create and authorize users in Azure AD, see the [Azure AD documentation](https://docs.microsoft.com/zh-cn/azure/active-directory/fundamentals).

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p44059.png)

## Step 1: Create an application in Azure AD

1.  Log on to the [Azure portal](https://portal.azure.com/?l=en.en-us#home) as an administrator.

2.  In the upper-left corner of the homepage, click the ![SSO_AAD_icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6420549951/p112037.png) icon.

3.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

4.  On the page that appears, click **New application**.

5.  Enter **Alibaba Cloud Service \(Role-based SSO\)** in the search box and select Alibaba Cloud Service \(Role-based SSO\).

6.  Enter a name for the application and click **Create**.

    The default application name **Alibaba Cloud Service \(Role-based SSO\)** is used in this example. You can also enter a custom name for the application.

7.  On the Alibaba Cloud Service \(Role-based SSO\) page, click **Properties** in the left-side navigation pane. Then, copy and save the **object ID** for subsequent use.


## Step 2: Configure SSO in Azure AD

1.  In the left-side navigation pane of the Alibaba Cloud Service \(Role-based SSO\) page, click **Single sign-on**.

2.  In the Select a single sign-on method section, click **SAML**.

3.  On the Set up Single Sign-On with SAML page, perform the following steps:

    1.  In the upper-left corner, click **Upload metadata file**, select a file, and then click **Add**.

        ![Upload a metadata file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p43731.png)

        **Note:** You can obtain the metadata file from the following URL: `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

    2.  In the **Basic SAML Configuration** section, set the following parameters and click **Save**.

        -   **Identifier \(Entity ID\)**: By default, the value of this parameter is set to the value of the `entityID` parameter that is read from the preceding metadata file.
        -   **Reply URL \(Assertion Consumer Service URL\)**: By default, the value of this parameter is set to the value of the `Location` that is read from the preceding metadata file.
        -   **Relay State**: Enter the URL of the Alibaba Cloud service page to which an Azure AD user is redirected after the user logs on to the Azure portal through SSO.

            **Note:** To ensure high security, you must enter a URL that points to an Alibaba website in the **Relay State** field. For example, you can enter one of the following domain names in the Relay State field: \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this field is left empty, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to Azure AD.

    3.  In the **User Attributes & Claims** section, click the ![Edit](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p112341.png) icon.

    4.  Click **Add new claim**, set the following parameters and click **Save**.

        -   Enter `Role` in the **Name** field.
        -   Enter `https://www.aliyun.com/SAML-Role/Attributes` in the **Namespace** field.
        -   Select **Attribute** from the **Source** drop-down list.
        -   Select `user.assignedroles` from the **Source attribute** drop-down list.
    5.  Repeat the preceding step to add another claim and set the required parameters.

        -   Enter `RoleSessionName` in the **Name** field.
        -   Enter `https://www.aliyun.com/SAML-Role/Attributes` in the **Namespace** field.
        -   Select **Attribute** from the **Source** drop-down list.
        -   Select `user.userprincipalname` from the **Source attribute** drop-down list.
    6.  In the **SAML Signing Certificate** section, click **Download** in the **Federation Metadata XML** field to obtain the related XML file.

        ![Download the related federation metadata XML file](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3660957061/p44054.png)


## Step 3: Create an IdP in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using Account1.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** page, click **Create IdP**.

4.  On the page that appears, set the **IdP Name** parameter to `AAD` and set the **Note** parameter based on your business requirements.

5.  In the **Metadata File** field, click **Upload**.

    **Note:** You must upload the **federation metadata XML** file that you have downloaded in [Step 2: Configure SSO in Azure AD](#section_hcw_ey6_57b).

6.  Click **OK**.


## Step 4: Create a RAM role in the Alibaba Cloud Management Console

1.  After the IdP is created, click **Create RAM Role**.

2.  On the page that appears, click **Create RAM Role**.

3.  In the Create RAM Role pane, set the Trusted entity type parameter to **IdP** and click **Next**.

4.  Set the **RAM Role Name** parameter to `AADrole` and set the **Note** parameter based on your business requirements.

5.  Select `AAD` from the Select IdP drop-down list and click **OK**.

    **Note:**

    -   You can grant permissions to the RAM role based on your business requirements. For more information, see [Grant permissions to a RAM role](/intl.en-US/RAM Role Management/Grant permissions to a RAM role.md).
    -   After you create the IdP and the RAM role, save the Alibaba Cloud Resource Names \(ARNs\) of the IdP and the RAM role for subsequent use. For more information about how to obtain the ARN of the RAM role, see [View the basic information of a RAM role](/intl.en-US/RAM Role Management/View the basic information of a RAM role.md).
6.  Click **Close**.


## Step 5: Associate the Alibaba Cloud RAM role with the Azure AD user

1.  Create a role in Azure AD.

    1.  Log on to the [Azure AD Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer) as an administrator.

    2.  Click the ![settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8707577061/p139775.png) icon next to the account.

    3.  Click **Select permissions**.

    4.  In the Permissions pane, select the following permissions and click **Consent**.

        ![Permissions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44135.png)

        **Note:** After the permissions are granted, you are redirected to Graph Explorer.

    5.  On the Graph Explorer page, select **GET** from the first drop-down list and select **beta** from the second drop-down list. Enter `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` in the search box next to the drop-down lists. Set the `objectID` parameter to the **object ID** that you saved on the Properties page in Step 1. Then, click **Run Query**.

        **Note:** If you have multiple directories, enter `https://graph.microsoft.com/beta/contoso.com/servicePrincipals` in the field next to the drop-down lists.

    6.  On the **Response Preview** tab, copy the `appRoles` property for subsequent use.

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

    7.  Go to **Graph Explorer**, select **PATCH** from the first drop-down list and select **beta** from the second drop-down list. Enter `https://graph.microsoft.com/beta/servicePrincipals/<objectID>` in the text box next to the drop-down lists. Set the `objectID` parameter to the **object ID** that you saved on the Properties page in Step 1. Copy and paste the following sample script into the **Request Body** section, edit the script based on your business requirements, and then click **Run Query**.

        ```
        { 
          "appRoles": [
            { 
              "allowedMemberTypes":[
                "User"
              ],
              "description": "msiam_access",
              "displayName": "msiam_access",
              "id": "7dfd756e-8c27-4472-b2b7-38c17fc5****",
              "isEnabled": true,
              "origin": "Application",
              "value": null
            },
            { "allowedMemberTypes": [
                "User"
            ],
            "description": "Admin,AzureADProd",
            "displayName": "Admin,AzureADProd",
            "id": "68adae10-8b6b-47e6-9142-6476078c****", // The custom ID.
            "isEnabled": true,
            "origin": "ServicePrincipal",
            "value": "acs:ram::187125022722****:role/aadrole,acs:ram::187125022722****:saml-provider/AAD"// The ARNs of the IdP and the RAM role.
            }
          ]
        }
        ```

        **Note:** You can create multiple RAM roles based on your business requirements. Azure AD sends ARNs of the RAM roles and the IdPs as the claim value in a SAML response. However, you can add new roles only after the `msiam_access` part of the patch operation.

2.  Perform the following steps to associate the RAM role with the Azure AD user u2:

    1.  Log on to the **Azure portal** as an administrator.

    2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

    3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.

    4.  In the left-side navigation pane, click **Users and groups**.

    5.  In the upper-left corner of the page, click **Add user**.

        ![Add a user](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44178.png)

    6.  On the page that appears, click **Users**, select u2 from the user list, and then click **Select**.

    7.  Click **Assign**.

    8.  View the assigned role.

        ![View the assigned role](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7420549951/p44185.png)

        **Note:** After you click Assign, the RAM role is assigned to the Azure AD user \(u2\). If multiple RAM roles are created, you must assign the required role to the Azure AD user. If you want to implement role-based SSO from Azure AD to multiple Alibaba Cloud accounts, repeat the preceding steps.


## Verify the role-based SSO configurations

1.  Query the user access URL.

    1.  Log on to the **Azure portal** as an administrator.

    2.  In the left-side navigation pane, choose **Azure Active Directory** \> **Enterprise applications** \> **All applications**.

    3.  In the **NAME** column, click **Alibaba Cloud Service \(Role-based SSO\)**.

    4.  In the left-side navigation pane, click **Properties** and obtain the specified **user access URL**.

        ![User access URL](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0644139061/p187951.png)

2.  After you obtain the **user access URL**, enter the URL in the address bar of a browser, and log on to the Azure portal by using u2.

    You are redirected to the page that is specified in **Relay State** parameter. If the **Relay State** parameter is not specified or invalid, you are redirected to the homepage of the Alibaba Cloud Management Console after you log on to the Azure portal.

    ![Successful role-based SSO](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0644139061/p187952.png)


