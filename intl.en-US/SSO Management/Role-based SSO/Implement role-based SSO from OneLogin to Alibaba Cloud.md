# Implement role-based SSO from OneLogin to Alibaba Cloud

This topic provides an example on how to implement role-based single sign-on \(SSO\) from OneLogin to Alibaba Cloud. The example describes the end-to-end role-based SSO process from a cloud identity provider \(IdP\) to Alibaba Cloud.

In this example, an enterprise has an Alibaba Cloud account, a OneLogin administrator account, and multiple OneLogin users. The enterprise wants the OneLogin users to use their OneLogin accounts to access Alibaba Cloud by using role-based SSO without the need to create RAM users in Alibaba Cloud.

For more information about OneLogin, see [OneLogin documentation](https://onelogin.service-now.com/support?id=kb_article&sys_id=296c5c6bdb1c889024c780c74b9619f0&kb_category=60231113dbff4700d5505eea4b9619a9).

## Step 1: Create an application in OneLogin

1.  Log on to [OneLogin](https://app.onelogin.com/login) as an administrator.

2.  In the left side of the profile picture, click **Administration** to go to the Administration page.

3.  In the top navigation bar, choose**Applications** \> **Applications**.

4.  In the upper-right corner of the Applications page, click **Add App**.

5.  On the Find Applications page, search for SAML Test Connector \(Advanced\).

6.  On the page that appears, click SAML Test Connector \(Advanced\). On the Add SAML Test Connector \(Advanced\) page, configure the parameters and click **Save**.

    In this example, set the **Display Name** parameter to `LoginToAliyun`. Use the default values for other parameters.

7.  On the page that appears, move the pointer over **More Actions** in the upper-right corner and select **SAML Metadata** from the drop-down list. The IdP metadata file is downloaded. Save the file to your computer.


## Step 2: Create an IdP in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account.

2.  In the left-side navigation pane, click **SSO**.

3.  On the **Role-based SSO** tab, click **Create IdP**.

4.  In the Create IdP panel, set the **IdP Name** parameter to OneLogin and configure the **Note** parameter.

5.  In the **Metadata File** section, click **Upload** to upload the IdP metadata file obtained from [Step 1: Create an application in OneLogin](#section_78j_9js_fuc).

6.  Click **OK**.

    View the details of the created IdP and record the Alibaba Cloud Resource Name \(ARN\) of the IdP for subsequent use.


## Step 3: Create a RAM role in the Alibaba Cloud Management Console

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using the Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, click **Create RAM Role**.

4.  In the Create RAM Role panel, set the Trusted entity type parameter to **IdP** and click **Next**.

5.  In the Configure Role step, configure the **RAM Role Name** and **Note** parameters. For example, you can set the RAM Role Name parameter to Reader-OneLogin.

6.  Select OneLogin that you created in [Step 2: Create an IdP in the Alibaba Cloud Management Console](#section_7fz_jfo_srq) for the Select IdP parameter, view the content in the Conditions section, and then click **OK**.

7.  In the Finish step, click **Close**.

    View the details of the created RAM role and record the ARN of the RAM role for subsequent use.


## Step 4: Configure the application in OneLogin

1.  Log on to [OneLogin](https://app.onelogin.com/login) as an administrator.

2.  Create a custom user attribute.

    1.  In the top navigation bar, choose **Users** \> **Users**.

    2.  On the Users page, move the pointer over **More Actions** in the upper-right corner and select **Custom user fields** from the drop-down list.

    3.  In the upper-right corner of the Custom User Fields page, click **New User Field**.

    4.  In the New User Field dialog box, configure the **Name** and **Shortname** parameters and click **Save**.

        In this example, set the **Name** parameter to `AliyunRoles for SSO` and the **Shortname** parameter to `AliyunRoles`.

3.  Configure the application.

    1.  In the top navigation bar, choose**Applications** \> **Applications**.

    2.  On the Applications page, click LoginToAliyun that you created in [Step 1: Create an application in OneLogin](#section_78j_9js_fuc).

    3.  In the left-side navigation pane of the page that appears, click **Configuration**.

    4.  In the Application details section, configure the following parameters and click **Save**.

        -   **RelayState**: Enter a URL. You are redirected to the URL after logon.

            **Note:** For security purposes, you must enter a URL that points to an Alibaba website for the **RelayState** parameter. For example, the domain name in the URL can be \*.aliyun.com, \*.hichina.com, \*.yunos.com, \*.taobao.com, \*.tmall.com, \*.alibabacloud.com, or \*.alipay.com. If this parameter is left empty, you are redirected to the homepage of the Alibaba Cloud Management Console after logon.

        -   **Audience \(EntityID\)**: Enter `urn:alibaba:cloudcomputing:international`.
        -   **Recipient**: Enter `https://signin.alibabacloud.com/saml-role/sso`.
        -   **ACS \(Consumer\) URL**: Enter `https://signin.alibabacloud.com/saml-role/sso`.
    5.  In the left-side navigation pane, click **Parameters**.

    6.  Click the ![Create icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2626542261/p269249.png) icon to create the first custom application attribute.

        1.  In the New Field dialog box, set the **Field name** parameter to `https://www.aliyun.com/SAML-Role/Attributes/Role`, select **Include in SAML assertion** and **Multi-value parameter**, and then click **Save**.
        2.  In the Edit Field https://www.aliyun.com/SAML-Role/Attributes/Role dialog box, select **Aliyun Roles for SSO \(Custom\)** from the first drop-down list and **Semicolon Delimited input \(Multi-value output\)** from the second drop-down list in the **Default if no value selected** section. Then, click **Save**.
    7.  Click the ![Create icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2626542261/p269249.png) icon again to create the second custom application attribute.

        1.  In the New Field dialog box, set the **Field name** parameter to `https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`, select **Include in SAML assertion**, and then click **Save**.
        2.  In the Edit Field https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName dialog box, select **Email** from the drop-down list in the **Value** section and click **Save** .

            **Note:** You can also select another value such as **Username** or **userPrincipalName** from the drop-down list in the **Value** section based on your business requirements.

    8.  In the upper-right corner of the page, click **Save**.


## Step 5: Create a user in OneLogin and assign the application to the user

1.  Log on to [OneLogin](https://app.onelogin.com/login) as an administrator.

2.  In the top navigation bar, choose **Users** \> **Users**.

3.  Create a user.

    **Note:** If you have a OneLogin user, skip this step.

    1.  In the upper-right corner of the Users page, click **New User**.

    2.  On the New User page, configure the parameters. For example, set the **First name** parameter to Jack, the **Last name** parameter to Lee, the **Username** parameter to jacklee, the **Email** parameter to jacklee@example.com, and then click **Save User**.

    3.  On the page that appears, move the pointer over **More Actions** in the upper-right corner and select **Change Password** from the drop-down list. Configure a password for the user and click **Update**.

4.  In the **Custom Fields** section of the page that appears, configure the **Aliyun Roles for SSO** parameter.

    The value of the **Aliyun Roles for SSO** parameter consists of the ARN of the RAM role and the ARN of the IdP. The ARNs are separated by commas \(,\). The value must be in the `acs:ram::<account_id>:role/RoleName,acs:ram::<account_id>:saml-provider/ProviderName` format. The ARN of the RAM role is obtained from [Step 3: Create a RAM role in the Alibaba Cloud Management Console](#section_efr_wq8_8lw), the ARN of the IdP is obtained from [Step 2: Create an IdP in the Alibaba Cloud Management Console](#section_7fz_jfo_srq), and <account\_id\> is the ID of the Alibaba Cloud account.

    **Note:** If a user corresponds to multiple RAM roles, you can configure more than one value. The values are separated by semicolons \(;\). For example, you can set `acs:ram::125022144354xxxx:role/reader-onelogin,acs:ram::125022144354xxxx:saml-provider/OneLogin;acs:ram::125022144354xxxx:role/administrator-onelogin,acs:ram::125022144354xxxx:saml-provider/OneLogin;acs:ram::158622887609xxxx:role/finance,acs:ram::158622887609xxxx:saml-provider/OneLogin2` for the Aliyun Roles for SSO parameter.

5.  Assign the application to the user.

    1.  On the Applications page, click the ![Create icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2626542261/p269249.png) icon.

    2.  Select LoginToAliyun created in [Step 1: Create an application in OneLogin](#section_78j_9js_fuc) and click **Continue**.

    3.  In the dialog box that appears, click **Save**.

6.  In the upper-right corner of the Users page, click **Save User**.

7.  Repeat [4](#step_2gd_q5i_m44) to [6](#step_myy_gbe_bi7) to configure the **Aliyun Roles for SSO** parameter for other users of the enterprise and assign LoginToAliyun to the users.


## Step 6: Test role-based SSO

1.  Log on to [OneLogin](https://app.onelogin.com/login) by using the user jacklee that is created in [Step 5: Create a user in OneLogin and assign the application to the user](#section_t6y_awl_g5w).

2.  Click LoginToAliyun.

    The logon succeeds if one of the following page appears: the page to which the URL entered for the **RelayState** parameter points or the homepage of the Alibaba Cloud Management Console.

    **Note:** If you configure more than one value for the Aliyun Roles for SSO parameter in [Step 5: Create a user in OneLogin and assign the application to the user](#section_t6y_awl_g5w), you must select a specific RAM role before you can access Alibaba Cloud.


