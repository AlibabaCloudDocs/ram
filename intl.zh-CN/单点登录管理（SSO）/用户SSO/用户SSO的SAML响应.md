# 用户SSO的SAML响应

本文为您介绍进行用户SSO时SAML响应中必须包含的元素，尤其是SAML断言中的元素。

## 背景信息

在基于SAML 2.0的SSO流程中，当企业用户在IdP登录后，IdP将根据SAML 2.0 HTTP-POST绑定的要求生成包含SAML断言的认证响应，并由浏览器（或程序）自动转发给阿里云。这个SAML断言会被用来确认用户登录状态并从中解析出登录的主体。因此，断言中必须包含阿里云要求的元素，否则登录用户的身份将无法被确认，导致SSO失败。

## SAML响应

请确保您的IdP向阿里云发出符合如下要求的SAML响应，每一个元素都必须要有，否则SSO将会失败。

```
<saml2p:Response>
    <saml2:Issuer>...</saml2:Issuer>
    <saml2p:Status>
        ...
    </saml2p:Status>
    <saml2:Assertion>
        <saml2:Issuer>...</saml2:Issuer>
        <ds:Signature>
            ...
        </ds:Signature>
        <saml2:Subject>
            <saml2:NameID>${NameID}</saml2:NameID>
            <saml2:SubjectConfirmation>
                ...
            </saml2:SubjectConfirmation>
        </saml2:Subject>
        <saml2:Conditions>
            <saml2:AudienceRestriction>
                <saml2:Audience>${Audience}</saml2:Audience>
            </saml2:AudienceRestriction>
        </saml2:Conditions>
        <saml2:AuthnStatement>
            ...
        </saml2:AuthnStatement>
    </saml2:Assertion>
</saml2p:Response>
```

## SAML断言中的元素说明

-   **SAML 2.0协议的通用元素**

    |元素|说明|
    |--|--|
    |`Issuer`|`Issuer`的值必须与您在阿里云用户SSO设置中上传的元数据文件中的`EntityID`匹配。|
    |`Signature`|阿里云要求SAML断言必须被签名以确保没有篡改，`Signature`及其包含的元素必须包含签名值、签名算法等信息。|
    |`Subject`|`Subject`必须包含以下元素：

    -   有且仅有一个`NameID`元素，是阿里云账号下的某个RAM用户的身份标识。详情请参见本文下面所述的NameID元素和NameID示例。
    -   有且仅有一个`SubjectConfirmation`元素，其中包含一个`SubjectConfirmationData`元素。`SubjectConfirmationData`必须有以下两个属性：

        -   `NotOnOrAfter`：规定SAML断言的有效期。
        -   `Recipient`：阿里云通过检查该元素的值来确保阿里云是该断言的目标接收方，其取值必须为`https://signin-intl.aliyun.com/${accountId}/saml/SSO`，`${accountId}`为阿里云账号ID。
以下是一个`Subject`元素的示例：

        ```
<Subject>
  <NameID Format="urn:oasis:names:tc:SAML:2.0:nameid-format:persistent">Alice@example.onaliyun.com</NameID>        
  <SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">   
    <SubjectConfirmationData NotOnOrAfter="2019-01-01T00:01:00.000Z" Recipient="https://signin-intl.aliyun.com/${accountId}/saml/SSO"/>    
  </SubjectConfirmation>
</Subject>
        ``` |
    |`Conditions`|在`Conditions`元素中，必须包含一个`AudienceRestriction`元素，其中可包含一至多个`Audience`元素，但必须有一个`Audience`元素的取值为 `https://signin-intl.aliyun.com/${accountId}/saml/SSO`，`${accountId}`为阿里云账号ID。

以下是一个`Conditions`元素的示例：

    ```
<Conditions>
  <AudienceRestriction>
    <Audience>https://signin-intl.aliyun.com/${accountId}/saml/SSO</Audience>
  </AudienceRestriction>
</Conditions>           
    ``` |

-   **NameID元素**

    阿里云需要通过UPN（User Principal Name）来定位一个RAM用户，所以要求企业IdP生成的SAML断言包含用户的UPN。阿里云通过解析SAML断言中的`NameID`元素，来匹配RAM用户的UPN从而实现用户SSO。

    因此，在配置IdP颁发的SAML断言时，需要将对应于RAM用户UPN的字段映射为SAML断言中的`NameID`元素。

    `NameID`元素必须是以下几种：

    -   使用**域别名**作为`NameID`元素的后缀，即`<username>@<domain_alias>`。其中`<username>`为RAM用户的用户名，`<domain_alias>`为域别名。关于如何设置域别名，请参见[创建并验证域别名](/intl.zh-CN/安全设置/高级设置/创建并验证域别名.md)。
    -   使用**辅助域名**作为`NameID`元素的后缀，即`<username>@<auxiliary_domain>`。其中`<username>`为RAM用户的用户名，`<auxiliary_domain>` 为辅助域名。关于如何设置辅助域名，请参见[进行用户SSO时阿里云SP的SAML配置](/intl.zh-CN/单点登录管理（SSO）/用户SSO/进行用户SSO时阿里云SP的SAML配置.md)。

        **说明：** 如果您同时设置了域别名和辅助域名，辅助域名将不会生效。此时，`NameID`元素只能使用域别名作为后缀。

    -   使用**默认域名**作为`NameID`元素的后缀，即`<username>@<default_domain>`。其中`<username>`为RAM用户的用户名，`<default_domain>`为默认域名。关于如何设置默认域名，请参见[管理默认域名](/intl.zh-CN/安全设置/高级设置/管理默认域名.md)。

        **说明：** 即使设置了域别名或辅助域名，仍可以使用默认域名作为`NameID`的后缀。

-   **NameID示例**

    RAM用户名为`Alice`，默认域名为`example.onaliyun.com`。

    -   如果设置了域别名为`example.com`，SAML断言中的`NameID`取值为`Alice@example.onaliyun.com`或`Alice@example.com`。
    -   如果没有设置域别名，设置了辅助域名为`example2.com`，SAML断言中的`NameID`取值为`Alice@example.onaliyun.com`或`Alice@example2.com`。
    -   如果设置了域别名为`example.com`后，又设置了辅助域名为`example2.com`，SAML断言中的`NameID`取值为`Alice@example.onaliyun.com`或`Alice@example.com`。注意此时辅助域名不生效。

