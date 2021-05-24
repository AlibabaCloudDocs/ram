# 进行角色SSO时企业IdP的SAML配置

进行角色SSO时，为了建立企业IdP对阿里云的信任，需要在企业IdP中配置阿里云为可信SAML服务提供商（SP）。

1.  从阿里云获取SAML服务提供商元数据URL。

    URL为`https://signin.alibabacloud.com/saml-role/sp-metadata.xml`。

2.  在企业IdP中创建一个SAML SP，并根据实际情况选择下面任意一种方式配置阿里云为信赖方。

    -   直接使用步骤[1](#step_yqv_e6o_kox)所述的阿里云元数据URL进行配置。
    -   如果您的IdP不支持URL配置，您可以步骤[1](#step_yqv_e6o_kox)所述URL下载元数据文件并上传至您的IdP。
    -   如果您的IdP不支持元数据文件上传，则需要手动配置以下参数：
        -   `Entity ID`：`urn:alibaba:cloudcomputing:international`
        -   `ACS URL`：`https://signin.alibabacloud.com/saml-role/sso`
        -   `RelayState`（可选）：如果您的IdP支持设置`RelayState`参数，您可以将其配置成SSO登录成功后希望跳转到的页面URL。如果不进行配置，SSO登录成功后，将会跳转到阿里云控制台首页。

            **说明：** 出于安全原因，您只能填写阿里巴巴旗下的域名URL作为`RelayState`的值，例如：\*.aliyun.com、\*.hichina.com、\*.yunos.com、\*.taobao.com、\*.tmall.com、\*.alibabacloud.com、\*.alipay.com。


在企业IdP中配置阿里云为可信SAML SP后，需要在企业IdP中配置SAML断言属性。更多信息，请参见[角色SSO的SAML响应](/intl.zh-CN/单点登录管理（SSO）/角色SSO/角色SSO的SAML响应.md)。

