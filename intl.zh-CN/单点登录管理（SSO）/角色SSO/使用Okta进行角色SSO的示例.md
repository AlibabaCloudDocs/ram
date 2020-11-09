# 使用Okta进行角色SSO的示例

本文提供一个以Okta与阿里云进行角色SSO的示例，帮助您理解企业IdP与阿里云进行SSO的端到端配置流程。

-   进行操作前，请确保您已经注册了阿里云账号。如还未注册，请先完成[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。
-   进行操作前，请确保您已经拥有Okta账号。

    **说明：** 如果仅作为测试用途，您可以在Okta官网申请有效期为30天的账号。


## 操作流程

本文的配置目标是在Okta应用中创建一个名为approle的属性，并根据这个属性的值来映射访问阿里云的RAM角色。您可以按照下图所示的操作流程完成阿里云、Okta的配置。

![流程图](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6790549951/p128782.png)

## 步骤1：在Okta创建支持SAML SSO的应用

1.  登录[Okta门户](https://www.okta.com/)。

    **说明：** 您需要提前在手机端下载Okta Verify应用，登录时需要输入6位动态验证码。

2.  将鼠标悬停在页面右上方的账号图标上，单击**Your Org**。

3.  单击**Admin**。

    ![SSO_Okta_管理员](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6790549951/p111967.png)

4.  在Okta顶部菜单栏，单击**Applications**。

    ![SSO_Okta_Applications](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6790549951/p111964.png)

5.  单击**Add Application**。

6.  单击**Create New App**。

7.  **Platform**选择为**Web**，**Sign on method**选择为**SAML 2.0**，单击**Create**。

8.  配置应用名称为role-sso-test，单击**Next**。

9.  配置SAML，然后单击**Next**。

    ![SAML General](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p129121.png)

    -   **Single sign on URL**：`https://signin.alibabacloud.com/saml-role/sso`。
    -   **Audience URI**：`urn:alibaba:cloudcomputing:international`。
    -   **Default RelayState**：用来配置用户登录成功后跳转到的阿里云页面。

        **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为**Default RelayState**的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com，否则配置无效。若不配置，默认跳转到阿里云控制台首页。

    -   **Name ID format**：选择**EmailAddress**。
    -   **Application username**：选择**Email**。
10. 根据需要选择合适的应用类型，单击**Finish**。


## 步骤2：在Okta获取SAML IdP元数据

1.  在Okta顶部菜单栏，单击**Applications**。

2.  单击目标应用名称（role-sso-test）。

3.  在**Sign On**页签下，单击**Identity Provider metadata**，将IdP元数据另存到本地。

    ![SSO_Okta_Sign On](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p111987.png)


## 步骤3：在阿里云创建身份提供商

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**SSO管理**。

3.  在**角色SSO**页签，单击**创建身份提供商**。

4.  输入**身份提供商名称**（okta-provider）和**备注**。

5.  单击**元数据文档**下的**上传文件**，上传从[步骤2：在Okta获取SAML IdP元数据](#section_gja_2u2_so7)中获取的IdP元数据。

6.  单击**确定**。


## 步骤4：在阿里云创建RAM角色

1.  在RAM控制台的左侧导航栏，单击**RAM角色管理**。

2.  单击**创建RAM角色**。

3.  选择可信实体类型为**身份提供商**，单击**下一步**。

4.  输入**角色名称**（admin）和**备注**。

5.  选择从[步骤3：在阿里云创建身份提供商](#section_7fz_jfo_srq)中创建的身份提供商并查看限制条件后，单击**完成**。

6.  单击**关闭**。


## 步骤5：在Okta配置Profile

1.  编辑Profile，创建一个新的Attribute。

    1.  在Okta顶部菜单栏，单击**Directory** \> **Profile Editor**。

    2.  单击对应Profile后面的![edit profile](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p128688.png)。

    3.  单击**Add Attribute**，填写Attribute信息。

        -   **Data type**：选择**string**。
        -   **Display name**：填写将在用户界面中显示的名称，本示例中请填写`approle`。
        -   **Variable name**：填写将在映射中引用的变量名称，本示例中请填写`approle`。您需要记录该参数的值，下一步配置Attribute的时候会用到。
        -   **Enum**：选中**Define enumerated list of values**，定义一个枚举值列表。

            **说明：** 我们使用**Enum**来确保用户只能使用预定义的属性值。您也可以不使用**Enum**，而获得更高的灵活性。

        -   **Attribute members**：填写枚举值列表，**Value**必须要与RAM中创建的角色名称相同，例如：admin、reader。
        -   **Description**：请根据需要填写属性描述，可以不填写。
        -   **Attribute Length**：本示例使用枚举值，因此不需要设置。如果您实际中未使用枚举值，请根据需要设置属性长度。
        -   **Attribute required**：选中**Yes**。
        -   **Scope**：不选中**User personal**。
    4.  单击**Save**。

2.  配置Attribute。

    1.  在Okta顶部菜单栏，单击**Applications** \> **Applications**。

    2.  单击应用名称（role-sso-test）。

    3.  在**General**页签下的**SAML Settings**区域，单击**Edit**。

    4.  在**Configure SAML**页面的**ATTRIBUTE STATEMENTS \(OPTIONAL\)**区域，配置如下图所示的两条数据。

        ![edit Attribute](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p128727.png)

        -   配置第1条数据：
            -   Name：填写`https://www.aliyun.com/SAML-Role/Attributes/RoleSessionName`。
            -   Value：选择**user.email**。
        -   配置第2条数据：
            -   Name：填写`https://www.aliyun.com/SAML-Role/Attributes/Role`。
            -   Value：取值为`String.replace("acs:ram::<account_id>:role/$approle,acs:ram::<account_id>:saml-provider/okta-provider", "$approle", appuser.approle)`，是用登录用户在应用Profile中的`approle`属性值来替换`$approle`占位符，从而获取最终的SAML属性值。其中`approle`是之前在Profile Attribute中定义的属性。`okta-provider`是[步骤3：在阿里云创建身份提供商](#section_7fz_jfo_srq)中创建的身份提供商。`<account_id>`需要替换为您的阿里云账号ID。例如：`String.replace("acs:ram::177242285274****:role/$approle,acs:ram::177242285274****:saml-provider/okta-provider", "$approle", appuser.approle)`。

## 步骤6：在Okta创建用户并分配应用

1.  创建用户。

    1.  在Okta顶部菜单栏，单击**Directory** \> **People**。

        ![OSS_Okta_poeple](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/7790549951/p113589.png)

    2.  单击**Add Person**，在**Add Person**页面，填写基本信息并将**Primary email**配置为被邀请用户的Email，例如：test@example.com。

    3.  在**Password**区域，勾选**Send user activation email now**，单击**Save**。

        **说明：** 根据页面提示激活Okta用户。

2.  分配应用。

    分配应用有以下两者方式，请任选其一。

    -   为单个用户分配应用。
        1.  在Okta顶部菜单栏，单击**Applications**。
        2.  单击目标应用名称（role-sso-test）后，在**Assignments**页签下，单击**Assign** \> **Assign to People**。
        3.  单击目标用户（test@example.com）后的**Assign**。
        4.  选择**approle**为admin。
        5.  单击**Save and Go Back**。
        6.  单击**Done**。
    -   将用户加入组，为组分配应用。

        1.  在Okta顶部菜单栏，先单击**Directory** \> **Groups**，然后单击**Add Group**，创建一个组。

            ![okta_group](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p130773.png)

        2.  单击组名称，然后单击**Manage People**，添加用户到组中。
        3.  在Okta顶部菜单栏，单击**Applications**。
        4.  单击目标应用名称（role-sso-test）后，在**Assignments**页签下，单击**Assign** \> **Assign to Groups**。
        5.  单击目标组后的**Assign**。
        6.  选择**approle**为admin。
        7.  单击**Save and Go Back**。
        8.  单击**Done**。
        **说明：** 如果一个用户属于多个组，生效的属性值只能有一个，即在应用的Assignments页签下第一个加入的组的相应属性会生效。如果用户所属的组发生变化，则会影响approle的取值。详情请参见[Okta用户指南](https://help.okta.com/en/prod/Content/index.htm)。


## 结果验证

1.  在Okta顶部菜单栏，单击**Applications** \> **Applications**。

2.  单击应用名称（role-sso-test）。

3.  在**General**页签下的**App Embed Link**区域，获取登录URL。

    ![App Embed Link](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p128977.png)

4.  打开另一个浏览器，输入获取到的URL，用test@example.com登录。

    如果成功跳转到您设置的`Default RelayState`对应页面（或默认的阿里云控制台首页），则说明登录成功。

    ![successful result](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p128774.png)


## （可选）在Okta中配置用户对应的多个角色

如果您需要让用户对应阿里云的多个角色，则必须使用Group Attribute Statement，借助Group Name进行配置。具体的配置方法如下：

1.  创建多个组。其组名应按照SAML断言中Role Attribute要求的格式，例如：acs:ram::177242285274\*\*\*\*:role/admin,acs:ram::177242285274\*\*\*\*:saml-provider/okta-provider。

    ![add group](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p128790.png)

2.  将test@example.com加入多个组。

3.  在应用的**SAML Settings**中，删除Role所对应的attribute statement，添加一个Group Attribute Statement，Filter应确保能够过滤出上述组名，例如：Start with acs:ram。

    ![group Attribute](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p128789.png)

4.  进行上述配置后，再次使用test@example.com登录阿里云时，该用户将会选择登录的角色。

    ![Role sign in](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8790549951/p129112.png)


关于Okta的相关操作，详情请参见[Okta用户指南](https://help.okta.com/en/prod/Content/index.htm)。

