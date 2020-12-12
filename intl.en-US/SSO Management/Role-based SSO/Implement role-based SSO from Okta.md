# Implement role-based SSO from Okta

This topic provides an example on how to implement role-based single sign-on \(SSO\) from Okta to Alibaba Cloud. The example describes the end-to-end SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud.

-   An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).
-   An Okta account is created.

    **Note:** A 30-day free trial is available for each Okta account.


## Procedure

In this example, an attribute named approle is added to the profile of an Okta application. The approle attribute is used to specify a Resource Access Management \(RAM\) role. The following figure shows the procedure to enable role-based SSO in Alibaba Cloud and Okta.

![Flowchart](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9690549951/p128782.png)

## Step 1: Create an application that supports SAML 2.0-based SSO in Okta

1.  Log on to the [Okta portal](https://www.okta.com/).

    **Note:** A dynamic 6-digit verification code is required for the logon. The verification code is provided by the Okta Verify app. Therefore, you must install the Okta Verify app on your mobile phone before the logon.

2.  In the upper-right corner of the Okta portal, click the account name and select **Your Org** from the drop-down list.

3.  In the upper-right corner of the page that appears, click **Admin**.

    ![SSO_Okta_Admin](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9690549951/p111967.png)

4.  In the top navigation bar, click **Applications**.

    ![SSO_Okta_Applications](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9690549951/p111964.png)

5.  On the page that appears, click **Add Application**.

6.  On the page that appears, click **Create New App**.

7.  In the dialog box that appears, set **Platform** to **Web** and **Sign on method** to **SAML 2.0**. Then, click **Create**.

8.  In the General Settings step, enter role-sso-test in the App name field and click **Next**.

9.  In the Configure SAML step, configure the parameters and click **Next**.

    ![SAML General](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0790549951/p129121.png)

    -   In the **Single sign on URL** field,enter `https://signin.alibabacloud.com/saml-role/sso`.
    -   In the **Audience URI** field,enter `urn:alibaba:cloudcomputing:international`.
    -   In the **Default RelayState** field, enter a URL. A user is redirected to the URL after logon.

        **Note:** In the **Default RelayState** field, you must enter a URL that points to an Alibaba website for security purposes. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this field is empty, you are redirected to the homepage of the Alibaba Cloud Management Console after logon.

    -   Select **EmailAddress** from the **Name ID format** drop-down list.
    -   Select **Email** from the **Application username** drop-down list.
10. Select an application type based on your business requirements and click **Finish**.


## Step 2: Download the SAML IdP metadata file of Okta

1.  In the top navigation bar of the Okta portal, click **Applications**.

2.  Click the application name role-sso-test.

3.  On the **Sign On** tab, click **Identity Provider metadata** to download the metadata file.

    ![SSO_Okta_Sign On](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0790549951/p111987.png)


## Step 3: Create an IdP in Alibaba Cloud

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** tab, click **Create IdP**.

4.  Enter okta-provider in the **IdP Name** field and enter a description of the IdP in the **Note** field.

5.  Click **Upload** under **Metadata File** to upload the SAML IdP metadata file that you downloaded in [Step 2: Download the SAML IdP metadata file of Okta](#section_gja_2u2_so7).

6.  Click **OK**.


## Step 4: Create a RAM role in Alibaba Cloud

1.  In the left-side navigation pane of the RAM console, click **RAM Roles**.

2.  On the page that appears, click **Create RAM Role**.

3.  In the panel that appears, set Trusted entity type to **IdP** and click **Next**.

4.  Enter admin in the **RAM Role Name** field and enter the description of the RAM role in the **Note** field.

5.  Select the IdP that you created in [Step 3: Create an IdP in Alibaba Cloud](#section_7fz_jfo_srq), view the conditions, and then click **OK**.

6.  Click **Close**.


## Step 5: Configure the profile of the application in Okta

1.  Add an attribute to the profile of the application.

    1.  In the top navigation bar, choose **Directory** \> **Profile Editor**.

    2.  Click the ![edit profile](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0790549951/p128688.png) icon next to the profile.

    3.  Click **Add Attribute**. In the Add Attribute dialog box, configure the attribute parameters.

        -   Select **string** from the **Data type** drop-down list.
        -   In the **Display name** field, enter `approle`. The name is displayed in the portal to represent the attribute.
        -   In the **Variable name** field, enter `approle`. The variable is used to specify the Alibaba Cloud RAM role. You must record the value of Variable name for subsequent use.
        -   Select **Define enumerated list of values** next to **Enum**.

            **Note:** If you select **Define enumerated list of values**, only enumeration values of the attribute are valid. You can clear **Enum** to increase flexibility.

        -   In the **Attribute members** section, specify an enumeration for the attribute. Each enumeration value must be the same as the name of a RAM role that you created in Alibaba Cloud. In this example, the values are admin and reader.
        -   Optional. In the **Description** field, enter a description of the attribute.
        -   In this example, you do not need to set **Attribute Length** because an enumeration value is configured for the attribute. If no enumeration values are configured for an attribute, set the attribute length.
        -   Select **Yes** next to **Attribute required**.
        -   Clear **User personal** next to **Scope**.
    4.  Click **Save**.

2.  Configure the attribute.

    1.  In the top navigation bar, choose **Applications** \> **Applications**.

    2.  Click the application name role-sso-test.

    3.  On the **General** tab, click **Edit** in the **SAML Settings** section.

    4.  In the **ATTRIBUTE STATEMENTS \(OPTIONAL\)** section of the **Configure SAML** page, specify the following two attribute statements:

        ![edit Attribute](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0790549951/p128727.png)

        -   Attribute statement 1
            -   Enter `https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName` in the Name column.
            -   Select **user.email** from the Value drop-down list.
        -   Attribute statement 2
            -   Enter `https://www.aliyun.com/SAML-Role/Attributes/Role` in the Name column.
            -   Select `String.replace("acs:ram::<account_id>:role/$approle,acs:ram::<account_id>:saml-provider/okta-provider", "$approle", appuser.approle)` from the Value drop-down list. Replace `$approle` with an enumeration value of `approle`. `approle` is the attribute that you added to the profile. `okta-provider` is the name of the IdP that you created in [Step 3: Create an IdP in Alibaba Cloud](#section_7fz_jfo_srq). Replace `<account_id>` with the ID of your Alibaba Cloud account. Example: `String.replace("acs:ram::177242285274****:role/$approle,acs:ram::177242285274****:saml-provider/okta-provider", "$approle", appuser.approle)`.

## Step 6: Add a user and assign the application to the user in Okta

1.  Add a user.

    1.  In the top navigation bar, choose **Directory** \> **People**.

        ![OSS_Okta_poeple](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1790549951/p113589.png)

    2.  On the People page, click **Add Person**. In the **Add Person** dialog box, enter the email address of the user to add in the **Primary email** field and configure other parameters. In this example, the email address is test@example.com.

    3.  Set **Password** to **Send user activation email now** and click **Save**.

        **Note:** Activate the Okta user as prompted.

2.  Assign the application to the user.

    You can use one of the following methods to assign the application.

    -   Assign the application to the user
        1.  In the top navigation bar, click **Applications**.
        2.  Click the application name role-sso-test. On the **Assignments** tab, choose **Assign** \> **Assign to People**.
        3.  In the dialog box that appears, click **Assign** next to the test@example.com user.
        4.  Select admin from the **approle** drop-down list.
        5.  Click **Save and Go Back**.
        6.  Click **Done**.
    -   Add the user to a group and assign the application to the group

        1.  In the top navigation bar, choose **Directory** \> **Groups**. On the page that appears, click **Add Group** to create a group.

            ![okta_group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1790549951/p130773.png)

        2.  Click the name of the group. On the page that appears, click **Manage People** to add the user to the group.
        3.  In the top navigation bar, click **Applications**.
        4.  Click the application name role-sso-test. On the **Assignments** tab, choose **Assign** \> **Assign to Groups**.
        5.  Click **Assign** next to the group.
        6.  Select admin from the **approle** drop-down list.
        7.  Click **Save and Go Back**.
        8.  Click **Done**.
        **Note:** If the user belongs to multiple groups, only one value of the approle attribute is used. The used attribute value is the value that is specified for the group to which the user is first added. If the user is added to or removed from groups, the value of the approle attribute changes. For more information, see [Okta Product Documentation](https://help.okta.com/en/prod/Content/index.htm).


## Test role-based SSO

1.  In the top navigation bar of the Okta portal, choose **Applications** \> **Applications**.

2.  Click the application name role-sso-test.

3.  In the **App Embed Link** section of the **General** tab, copy the logon URL.

    ![App Embed Link](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1790549951/p128977.png)

4.  Open a new browser, paste the logon URL in the address bar, and then press Enter. On the logon page, use test@example.com to log on.

    The logon is successful if the following page appears: the page to which the URL specified by the `Default RelayState` field points or the homepage of the Alibaba Cloud Management Console.

    ![successful result](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1790549951/p128774.png)


## \(Optional\) Assign multiple roles to a user in Okta

If you want to assign multiple roles to a user in Okta, you must create multiple user groups in the required format and create a group attribute statement. To assign multiple roles to a user in Okta, perform the following steps:

1.  Create multiple groups. Each group name must follow the same format as a value of the role attribute in the SAML assertion. For example, you can set the name of a group to acs:ram::177242285274\*\*\*\*:role/admin,acs:ram::177242285274\*\*\*\*:saml-provider/okta-provider.

    ![add group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2790549951/p128790.png)

2.  Add the test@example.com user to the groups.

3.  Delete the attribute statements of RAM roles from the **SAML Settings** section of the application. Create a group attribute statement. Make sure that the filter condition can be used to filter all the group names. For example, you can set the filter to Start with acs:ram.

    ![group Attribute](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2790549951/p128789.png)

4.  After the configurations are complete, log on to the Alibaba Cloud Management Console as the test@example.com user. You are prompted to select a role to assume.

    ![Role sign in](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2790549951/p129112.png)


For more information about how to use Okta, see [Okta Product Documentation](https://help.okta.com/en/prod/Content/index.htm).

