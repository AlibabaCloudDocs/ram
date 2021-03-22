# Implement role-based SSO by using Active Directory Federation Services

This topic provides an example of how to implement the role-based single sign-on \(SSO\) feature between Alibaba Cloud and Active Directory Federation Services \(AD FS\). This topic also describes how to implement end-to-end identity SSO between a cloud identity provider \(IdP\) and Alibaba Cloud.

You can use AD FS to manage your users and configure enterprise applications such as Alibaba Cloud. After role-based SSO is configured, your AD administrators can control user access to Alibaba Cloud. In this example, you have two Alibaba Cloud accounts \(Account1 and Account2\) and four AD user groups \(Aliyun-<account-id\>-ADFS-Admin and Aliyun-<account-id\>-ADFS-Reader\). An employee's AD user account named Alice belongs to these groups. You need to implement role-based SSO from AD FS to Account1 and Account2.

**Note:** <account-id\> in the name of each user group refers to the ID of Account1 or Account2.

## SSO process

The following figure shows the process of role-based SSO.

![Process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p40996.png)

After an AD administrator completes the configurations of role-based SSO, Alice can log on to the Alibaba Cloud console based on the process. For more information, see [Overview of role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Overview of role-based SSO.md).

The SSO process shows that users can be authenticated without the need to provide Alibaba Cloud usernames and passwords during logon.

## Configure AD FS as a trusted SAML IdP in Alibaba Cloud

1.  Log on to the Alibaba Cloud RAM console by using Account1. Create an IdP named `ADFS` and upload a metadata file. You can obtain the metadata file of AD FS from the URL: `https://<ADFS-server>/federationmetadata/2007-06/federationmetadata.xml`.

    **Note:** <ADFS-server\> in the URL is the domain name or IP address of your AD FS server.

    For more information, see [Configure the SAML settings of Alibaba Cloud for role-based SSO](/intl.en-US/SSO Management/Role-based SSO/Configure the SAML settings of Alibaba Cloud for role-based SSO.md).

2.  Create two RAM roles named ADFS-Admin and ADFS-Reader. When you create the roles, select IdP for the Trusted entity type parameter and select `ADFS` from the Select IdP drop-down list. Then, attach the `AdministratorAccess` policy to the ADFS-Admin role and attach the `ReadOnlyAccess` policy to the ADFS-Reader role.

    For more information, see [Create a RAM role for a trusted IdP](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted IdP.md).

3.  Repeat the preceding steps to create an IdP and two RAM roles for Account2 and attach policies to the RAM roles.


**Note:** After you complete the configurations, Account1 and Account2 will trust the user identity and role information that are included in Security Assertions Markup Language \(SAML\) requests sent from your AD FS server.

## Configure Alibaba Cloud as a trusted SAML SP in AD FS

In AD FS, a SAML service provider \(SP\) is also known as a **relying party**. To configure Alibaba Cloud as a trusted SAML SP in AD FS, perform the following steps:

1.  On the **Server Manager** page, choose **Tools** \> **AD FS Management**.

2.  Select **Add Relying Party Trust**.****

    ![Add Relying Party Trust](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41011.png)

3.  Specify the SAML SP metadata of Alibaba Cloud for the relying party. The metadata URL is `https://signin.alibabacloud.com/saml-role/sp-metadata.xml`.

    ![Select Data Source](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41012.png)

4.  Complete the configurations as instructed.


## Configure SAML assertion attributes for the Alibaba Cloud SP

The SAML assertion that is issued by AD FS must contain the attributes, such as `NameID`, `Role`, and `RoleSessionName`. AD FS can provide these attributes by issuing transform rules.

-   `NameID`

    Perform the following steps to set the Windows account name of AD to the value of the `NameID` attribute in the SAML assertion:

    1.  Right-click the display name of the relying party and select **Edit Claim Rules**.
    2.  Click **Issuance Transform Rules**.

        **Note:** Issuance transform rules indicate how to transform a known user attribute and issue it as an attribute in the SAML assertion. You need to issue the Windows account name of a user in AD as `NameID`. Therefore, you need to add a new rule.

    3.  Select **Transform an Incoming Claim** from the **Claim rule template** drop-down list.

        ![Transform an Incoming Claim](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41035.png)

    4.  Specify the following parameters for the claim rule, and click **Finish**.

        -   Set the **Claim rule name** parameter to NameID.
        -   Set the **Incoming claim type** parameter to Windows account name.
        -   Set the **Outgoing claim type** parameter to Name ID.
        -   Set the **Outgoing name ID format** parameter to Persistent Identifier.
        -   Select the **Pass through all claim values** option.
        ![Configure Rule](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41044.png)

        After you have configured the required settings, AD FS will send the `NameID` attribute to Alibaba Cloud. The following code shows an example:

        ```
        <NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent">
            YourDomain\rolessouser
        </NameID>
        ```

-   `RoleSessionName`

    Perform the following steps to set the value of the `RoleSessionName` attribute in the SAML assertion to be the User Principal Name \(UPN\) of AD:

    1.  Click **Add Transform Claim Rule**.
    2.  Select **Send LDAP Attributes as Claims** from the **Claim rule template** drop-down list.

        ![Select Rule Template](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41064.png)

    3.  Specify the following parameters for the claim rule, and click **Finish**.

        -   Set the **Claim rule name** parameter to RoleSessionName.
        -   Select Active Directory from the **Attribute store** drop-down list.
        -   Select User-Principal-Name in the **LDAP Attribute** column. You can select another option as required, for example, Email.
        -   Select `https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName` in the **Outgoing Claim Type** column.
        ![Configure Rule](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41065.png)

    After you have configured the required settings, AD FS will send the `RoleSessionName` attribute to Alibaba Cloud. The following code shows an example.

    ```
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName">
        <AttributeValue>rolessouser@example.com<AttributeValue>
    </Attribute>
    ```

-   `Role`

    Perform the following steps to configure a custom attribute whose value contains the name of the Alibaba Cloud RAM role that is associated with the AD group of the user:

    1.  Click **Add Transform Claim Rule**.
    2.  Select **Send Claims Using a Custom Rule** from the **Claim rule template** drop-down list and click **Next**.

        ![Send Claims Using a Custom Rule](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1420549951/p41066.png)

    3.  Specify the following parameters for the claim rule, and click **Finish**.

        -   Set the **Claim rule name** parameter to Get AD Groups.
        -   Set the **Custom rule** parameter. The following code shows an example.

            ```
            c:[Type =="http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => add(store = "Active Directory",types = ("http://temp/variable"), query = ";tokenGroups;{0}", param =c.Value);
            ```

        ![Custom rule](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2420549951/p41067.png)

        **Note:** This rule is used to obtain the AD group to which the user belongs. The rule is saved in the http://temp/variable intermediate variable.

    4.  Click **Add Transform Claim Rule**.
    5.  Repeat the preceding steps to create a custom rule, specify the following parameters for the rule, and then click **Finish**.

        -   Set the **Claim rule name** parameter to Role.
        -   Set the **Custom rule** parameter. The following code shows an example.

            ```
            c:[Type == "http://temp/variable", Value =~ "(?i)^Aliyun-([\d]+)"] => issue(Type = "https://www.aliyun.com/SAML-Role/Attributes/Role",Value = RegExReplace(c.Value, "Aliyun-([\d]+)-(.+)", "acs:ram::$1:role/$2,acs:ram::$1:saml-provider/ADFS"));
            ```

        ![Choose Rule Type](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2420549951/p41109.png)

        **Note:** Based on this rule, if the user belongs to the Aliyun-<account-id\>-ADFS-Admin or Aliyun-<account-id\>-ADFS-Reader group, a SAML attribute will be generated and sent to Alibaba Cloud to match the RAM role ADFS-Admin or ADFS-Reader.

    After you have configured the required settings, your IdP will return a SAML assertion to Alibaba Cloud. The following code shows an example.

    ```
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/Role">
        <AttributeValue>acs:ram::<account-id>:role/ADFS-Admin,acs:ram::<account-id>:saml-provider/ADFS</AttributeValue>
    </Attribute>
    ```


## Test user-based SSO

1.  Log on to the AD FS SSO portal \(URL: `https://<ADFS-server>/adfs/ls/IdpInitiatedSignOn.aspx`\). Select the Alibaba Cloud application, and enter the username and password.

    **Note:** <ADFS-server\> in the URL is the domain name or IP address of your AD FS server. If the URL is unavailable, run the `Set-AdfsProperties -EnableIdpInitiatedSignonPage $True` command in PowerShell.

    ![Test user-based SSO](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2420549951/p41111.png)

2.  On the Role-based SSO page of Alibaba Cloud, select the target role and click **Sign In**.

    **Note:** If your user belongs to only one AD group, the user corresponds to only one role in Alibaba Cloud. In this case, the user can log on to the Alibaba Cloud Management Console without the need to select a role.

    ![Role-based SSO](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2420549951/p41794.png)


