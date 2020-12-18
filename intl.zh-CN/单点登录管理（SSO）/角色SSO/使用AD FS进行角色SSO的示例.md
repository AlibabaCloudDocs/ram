# 使用AD FS进行角色SSO的示例

本文提供一个以AD FS与阿里云进行SSO的示例，帮助用户理解企业IdP与阿里云进行SSO的端到端配置流程。

企业使用Active Directory （AD）进行员工管理，并通过AD FS配置包括阿里云在内的企业应用。AD管理员通过员工的用户组来管理员工对阿里云账号的访问权限。在本示例中，企业拥有两个阿里云账号（Account1和Account2），要管理的权限为Admin和Reader，企业员工用户名为Alice，该用户所在的AD用户组为Aliyun-<account-id\>-ADFS-Admin和Aliyun-<account-id\>-ADFS-Reader，企业要实现从AD FS到Account1和Account2的角色SSO。

**说明：** <account-id\>为云账号Account1或Account2的账号ID，因此用户Alice所在的AD用户组共4个，分别对应两个云账号中的Admin和Reader权限。

## 基本流程

员工进行控制台登录的基本流程如下图所示。

![基本流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7075217951/p40996.png)

AD管理员在完成角色联合登录的配置后，企业员工（Alice）可以通过如图所示的方法登录到阿里云控制台。详情请参见[进行角色SSO](/intl.zh-CN/单点登录管理（SSO）/角色SSO/进行角色SSO.md)。

上述过程表示，用户登录时，企业会进行统一登录认证，无需用户提供在阿里云上的任何用户名和密码。

## 在阿里云中将AD FS配置为可信SAML IdP

1.  在阿里云RAM控制台创建一个名为`ADFS`的身份提供商，并配置相应的元数据。AD FS的元数据URL为`https://<ADFS-server>/federationmetadata/2007-06/federationmetadata.xml`。

    **说明：** <ADFS-server\>是您的AD FS服务器域名或IP地址。

    详情请参见[进行角色SSO时阿里云SP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/角色SSO/进行角色SSO时阿里云SP的SAML配置.md)。

2.  在阿里云账号Account1中创建两个可信实体类型为身份提供商的RAM角色（ADFS-Admin和ADFS-Reader），选择刚刚创建的`ADFS`作为可信身份提供商，并对两个角色分别赋予`AdministratorAccess`和`ReadOnlyAccess`权限。

    详情请参见[创建可信实体为身份提供商的RAM角色](/intl.zh-CN/角色管理/创建RAM角色/创建可信实体为身份提供商的RAM角色.md)。

3.  使用同样的方法在Account2中创建同样的身份提供商和角色。


**说明：** 配置完成后，企业的阿里云账号将信任企业AD FS发来的SAML请求中的用户身份和角色信息。

## 在AD FS中将阿里云配置为可信SAML SP

在AD FS中，SAML SP被称作**信赖方（Relying Party）**。设置阿里云作为AD FS的可信SP的操作步骤如下。

1.  在**服务器管理器**的**工具**菜单中选择**AD FS管理**。

2.  在**AD FS**管理工具中**添加信赖方信任**。

    ![添加信赖方信任向导](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7075217951/p41011.png)

3.  为新创建的信赖方设置阿里云的角色SSO的SAML SP元数据，元数据URL为`https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。

    ![选择数据源](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7075217951/p41012.png)

4.  按照向导完成配置。


## 为阿里云SP配置SAML断言属性

阿里云需要AD FS在SAML断言中提供`NameID`、`Role`和`RoleSessionName`属性。AD FS中通过颁发转换规则来实现这一功能。

-   `NameID`

    配置Active Directory中的Windows账户名为SAML断言中的`NameID`，其操作步骤如下。

    1.  为信赖方**编辑声明规则**。
    2.  添加**颁发转换规则**。

        **说明：** 颁发转换规则（Issuance Transform Rules）：指如何将一个已知的用户属性，经过转换后，颁发为SAML断言中的属性。由于我们要将用户在AD中的Windows账户名颁发为`NameID`，因此需要添加一个新的规则。

    3.  **声明规则模版**选择**转换传入声明**。

        ![转换传入声明](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7075217951/p41035.png)

    4.  使用如下配置规则，并点击**完成**。

        -   **声明规则名称**：NameID
        -   **传入声明类型**：Windows账户名
        -   **传出声明类型**：名称ID
        -   **传出名称ID格式**：永久标识符
        -   **传递所有声明值**：勾选
        ![配置规则](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41044.png)

        配置完成后，AD FS将发送阿里云需要的`NameID`格式。

        ```
        <NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent">
            YourDomain\rolessouser
        </NameID>
        ```

-   `RoleSessionName`

    配置Active Directory中的UPN为SAML断言中的`RoleSessionName`，其操作步骤如下。

    1.  单击**添加转换声明规则**。
    2.  从**声明规则模板**中选择**以声明方式发送LDAP特性**。

        ![选择规则模板](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41064.png)

    3.  使用如下配置规则，并点击**完成**。

        -   **声明规则名称**：RoleSessionName
        -   **特性存储**：Active Directory
        -   **LDAP 特性列**：User-Principal-Name（您也可以根据具体需求选择其他属性，例如email。）
        -   **传出声明类型**：`https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`
        ![配置规则](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41065.png)

    配置完成后，AD FS将发送阿里云需要的`RoleSessionName`格式。

    ```
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName">
        <AttributeValue>rolessouser@example.com<AttributeValue>
    </Attribute>
    ```

-   `Role`

    通过自定义规则将特定的用户所属组的信息转化成阿里云上的角色名称，其操作步骤如下。

    1.  单击**添加转换声明规则**。
    2.  从**声明规则模板**中选择**使用自定义规则发送声明**，点击**下一步**。

        ![使用自定义规则发送声明](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41066.png)

    3.  使用如下配置规则，并点击**完成**。

        -   **声明规则名称**：Get AD Groups
        -   **自定义规则**：

            ```
            c:[Type =="http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => add(store = "Active Directory",types = ("http://temp/variable"), query = ";tokenGroups;{0}", param =c.Value);
            ```

        ![自定义规则](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41067.png)

        **说明：** 这个规则获取用户在AD中所属组的信息，保存在中间变量http://temp/variable中。

    4.  单击**添加转换声明规则**。
    5.  重复以上步骤，并点击**完成**。

        -   **声明规则名称**：Role
        -   **自定义规则**：

            ```
            c:[Type == "http://temp/variable", Value =~ "(?i)^Aliyun-([\d]+)"] => issue(Type = "https://www.aliyun.com/SAML-Role/Attributes/Role",Value = RegExReplace(c.Value, "Aliyun-([\d]+)-(.+)", "acs:ram::$1:role/$2,acs:ram::$1:saml-provider/ADFS"));
            ```

        ![选择规则类型](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41109.png)

        **说明：** 根据这个规则，如果用户所属的AD组中包含Aliyun-<account-id\>-ADFS-Admin或Aliyun-<account-id\>-ADFS-Reader，则将生成一个SAML属性，映射到阿里云上的角色ADFS-Admin或ADFS-Reader。

    配置完成后，IdP将返回阿里云所需要的SAML断言片段，如下所示。

    ```
    <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/Role">
        <AttributeValue>acs:ram::<account-id>:role/ADFS-Admin,acs:ram::<account-id>:saml-provider/ADFS</AttributeValue>
    </Attribute>
    ```


## 配置验证

1.  登录AD FS SSO门户（URL：`https://<ADFS-server>/adfs/ls/IdpInitiatedSignOn.aspx`），选择阿里云应用，输入用户名密码。

    **说明：** <ADFS-server\>是您的AD FS服务器域名或IP地址。如果网页不可用，可以通过PowerShell开启：`Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`。

    ![配置验证](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41111.png)

2.  在阿里云角色SSO页面，选择一个您要登录的角色，单击**登录**。

    **说明：** 如果您的用户在AD中只加入了一个组，则在阿里云上只会对应一个角色，该用户将直接登录，无需选择角色。

    ![阿里云角色SSO页面](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8075217951/p41794.png)


