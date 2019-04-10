# 使用 AD FS 进行角色 SSO 示例 {#concept_bpk_3jc_mfb .concept}

本文提供一个以 AD FS 与阿里云进行 SSO 的示例，帮助用户理解企业 IdP 与阿里云进行 SSO 的端到端配置流程。

## 场景 {#section_i32_zdd_mfb .section}

企业使用 Active Directory （AD）进行员工管理，并通过 AD FS 配置包括阿里云在内的企业应用。AD 管理员通过员工的用户组来管理员工对阿里云账号的访问权限。在本例中，企业拥有两个阿里云账号（Account1 和 Account2），要管理的权限为 Admin 和 Reader，企业员工用户名为 Alice，该用户所在的 AD 用户组为 Aliyun-<account-id\>-ADFS-Admin 和 Aliyun-<account-id\>-ADFS-Reader，企业想要实现从 AD FS 到 Account1 和 Account2 的 SSO。

**说明：** <account-id\>为云账号 Account1 或 Account2 的账号 ID，因此用户 Alice 所在的 AD 用户组共4个，分别对应两个云账号中的 Admin 和 Reader 权限。

员工进行控制台登录的基本流程如下图所示：

![基本流程](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410240996_zh-CN.png)

AD 管理员在完成角色联合登录的配置后，企业员工（Alice）可以通过如图所示的方法登录到阿里云控制台。详情请参见[角色 SSO 概述](intl.zh-CN/用户指南/身份集成/（邀测中）角色 SSO/角色 SSO 概述.md#)。

上述过程表示，用户登录时，企业会进行统一登录认证，无需用户提供在阿里云上的任何用户名和密码。

## 配置步骤 {#section_k32_zdd_mfb .section}

为了实现上述登录过程，管理员需要在阿里云和 AD FS 上进行以下配置：

-   在阿里云中将 AD FS 配置为可信 SAML IdP。

    1.  在阿里云 RAM 控制台创建一个名为`ADFS`的身份提供商，并配置相应的元数据。AD FS 的元数据 URL 为：`https://<ADFS-server>/federationmetadata/2007-06/federationmetadata.xml`。

        **说明：** <ADFS-server\>是您的 AD FS 服务器域名或 IP 地址。

        详情请参见[阿里云角色 SSO 的 SAML 配置](intl.zh-CN/用户指南/身份集成/（邀测中）角色 SSO/阿里云角色 SSO 的 SAML 配置.md#)。

    2.  在阿里云账号 Account1 中创建两个可信实体类型为身份提供商的 RAM 角色（ADFS-Admin 和 ADFS-Reader），选择刚刚创建的`ADFS`作为可信身份提供商，并对两个角色分别赋予`AdministratorAccess`和`ReadOnlyAccess`权限。详情请参见[管理 RAM 角色](intl.zh-CN/用户指南/身份管理/RAM 角色身份/管理 RAM 角色.md#)。
    3.  使用同样的方法在 Account2 中创建同样的身份提供商和角色。
    **说明：** 配置完成后，企业的阿里云账号将信任企业 AD FS 发来的 SAML 请求中的用户身份和角色信息。

-   在 AD FS 中将阿里云配置为可信 SAML SP。

    在 AD FS 中，SAML SP 被称作**信赖方（Relying Party）**。设置阿里云作为 AD FS 的可信 SP 的操作步骤如下：

    1.  在**服务器管理器**的**工具**菜单中选择**AD FS 管理**。
    2.  在 **AD FS** 管理工具中**添加信赖方信任**。

        ![添加信赖方信任向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410241011_zh-CN.png)

    3.  为新创建的信赖方设置阿里云的角色 SSO 的 SAML SP 元数据，元数据 URL为`https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。

        ![添加信赖方信任向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410241012_zh-CN.png)

    4.  按照向导完成配置。
-   为阿里云 SP 配置 SAML 断言属性。

    阿里云需要 AD FS 在 SAML 断言中提供`NameID`，`Role`，`RoleSessionName`属性。AD FS 中通过颁发转换规则来实现这一功能。

    -   `NameID`

        配置 Active Directory 中的 Windows 账户名为 SAML 断言中的`NameID`，其操作步骤如下：

        1.  为信赖方**编辑声明规则**。
        2.  添加**颁发转换规则**。

            **说明：** 颁发转换规则（Issuance Transform Rules）：指如何将一个已知的用户属性，经过转换后，颁发为 SAML 断言中的属性。由于我们要将用户在 AD 中的 Windows 账户名颁发为`NameID`，因此需要添加一个新的规则。

        3.  **声明规则模版**选择**转换传入声明**。

            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410241035_zh-CN.png)

        4.  使用如下配置规则，并点击**完成**。

            -   **声明规则名称**：NameID
            -   **传入声明类型**：Windows 账户名
            -   **传出声明类型**：名称 ID
            -   **传出名称 ID 格式**：永久标识符
            -   **传递所有声明值**：勾选
            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410241044_zh-CN.png)

            配置完成后，AD FS 将发送阿里云需要的`NameID`格式，如下：

            ```
            
            <NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent">
                YourDomain\rolessouser
            </NameID>
            
            ```

    -   `RoleSessionName`

        配置 Active Directory 中的 UPN 为 SAML 断言中的`RoleSessionName`，其操作步骤如下：

        1.  单击**添加转换声明规则**。
        2.  从**声明规则模板**中选择**以声明方式发送 LDAP 特性**。

            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341064_zh-CN.png)

        3.  使用如下配置规则，并点击**完成**。

            -   **声明规则名称**：RoleSessionName
            -   **特性存储**：Active Directory
            -   **LDAP 特性列**：User-Principal-Name（您也可以根据具体需求选择其他属性，如 Email。）
            -   **传出声明类型**：`https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`
            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341065_zh-CN.png)

        配置完成后，AD FS 将发送阿里云需要的`RoleSessionName`格式，如下：

        ```
        
        <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName">
            <AttributeValue>rolessouser@example.com<AttributeValue>
        </Attribute>
        
        ```

    -   `Role`

        通过自定义规则将特定的用户所属组的信息转化成阿里云上的角色名称。其操作步骤如下：

        1.  单击**添加转换声明规则**。
        2.  从**声明规则模板**中选择**使用自定义规则发送声明**，点击**下一步**。

            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341066_zh-CN.png)

        3.  使用如下配置规则，并点击**完成**。

            -   **声明规则名称**：Get AD Groups。
            -   **自定义规则**：

                ```
                
                c:[Type ==
                "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccount
                name", Issuer == "AD AUTHORITY"] => add(store = "Active Directory",
                types = ("http://temp/variable"), query = ";tokenGroups;{0}", param =
                c.Value);
                ```

            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341067_zh-CN.png)

            **说明：** 这个规则获取用户在 AD 中所属组的信息，保存在中间变量http://temp/variable中。

        4.  单击**添加转换声明规则**。
        5.  重复以上步骤，并点击**完成**。

            -   **声明规则名称**：Role。
            -   **自定义规则**：

                ```
                
                c:[Type == "http://temp/variable", Value =~ "(?i)^Aliyun-([\d]+)"]
                 => issue(Type = "https://www.aliyun.com/SAML-Role/Attributes/Role",
                Value = RegExReplace(c.Value, "Aliyun-([\d]+)-(.+)", "acs:ram::
                $1:role/$2,acs:ram::$1:saml-provider/ADFS"));
                ```

            ![添加转换声明规则向导](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341109_zh-CN.png)

            **说明：** 根据这个规则，如果用户所属的 AD 组中包含 Aliyun-<account-id\>-ADFS-Admin 或 Aliyun-<account-id\>-ADFS-Reader，则将生成一个 SAML 属性，映射到阿里云上的角色 ADFS-Admin 或 ADFS-Reader。

        配置完成后 IdP 将返回阿里云所需要的 SAML 断言，片段如下：

        ```
        
        <Attribute Name="https://www.aliyun.com/SAML-Role/Attributes/Role">
            <AttributeValue>acs:ram::<account-id>:role/ADFS-Admin,acs:ram::<account-id>:saml-provider/ADFS</AttributeValue>
        </Attribute>
        
        ```


## 配置验证 {#section_gw4_ry4_dhb .section}

1.  登录 AD FS SSO 门户（URL：`https://<ADFS-server>/adfs/ls/IdpInitiatedSignOn.aspx`），选择阿里云应用，输入用户名密码。

    **说明：** <ADFS-server\>是您的 AD FS 服务器域名或 IP 地址。如果网页不可用，可以通过 PowerShell 开启：`Set-AdfsProperties –EnableIdpInitiatedSignonPage $True`。

    ![AD FS SSO 门户](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341111_zh-CN.png)

2.  在阿里云角色 SSO 页面，选择一个您要登录的角色，单击**登录**。

    **说明：** 如果您的用户在 AD 中只加入了一个组，则在阿里云上只会对应一个角色，该用户将直接登录，无需选择角色。

    ![阿里云角色 SSO 页面](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136751/155486410341794_zh-CN.png)


