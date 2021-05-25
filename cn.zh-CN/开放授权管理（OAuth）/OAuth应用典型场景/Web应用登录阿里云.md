# Web应用登录阿里云

本文介绍Web应用如何通过OAuth 2.0扮演登录用户访问阿里云API。

-   Web应用扮演登录用户访问阿里云首先需要创建应用，为应用提供恰当的名称、OAuth范围、回调地址等关键信息，详情请参见[创建应用](/cn.zh-CN/开放授权管理（OAuth）/管理OAuth应用/创建应用.md)。应用创建成功后，您可以在应用列表中查看应用ID（client\_id），如下图所示。

    ![应用ID](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780932951/p127276.png)

    **说明：** 应用创建成功之后，可以在阿里云账号内直接扮演用户。如果要扮演其他阿里云账号的用户，需要获得其他阿里云账号的授权。

-   创建应用密钥，详情请参见[创建应用密钥](/cn.zh-CN/开放授权管理（OAuth）/管理OAuth应用/创建应用密钥.md)。应用密钥（client\_secret）只在创建时显示，不支持查询，请妥善保管。

## 基本流程

![基本流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9780932951/p14349.png)

1.  用户通过浏览器登录Web应用。

2.  Web应用重定向到阿里云OAuth 2.0服务并将URL返回给浏览器。

    **说明：** 如果用户还未登录，则会进一步重定向到阿里云登录服务。

3.  用户通过浏览器登录阿里云OAuth 2.0服务并申请授权码。

4.  阿里云OAuth 2.0服务重定向到Web应用并返回授权码给浏览器。

5.  浏览器通过Web应用使用授权码向阿里云OAuth 2.0服务申请代表用户身份的令牌。

    -   如何获取访问令牌，请参见[获取访问令牌](#section_03)。
    -   如何获取新的访问令牌，请参见[获取新的访问令牌](#section_04)。
    -   如何撤销刷新令牌，请参见[撤销刷新令牌](#section_05)。
6.  阿里云OAuth 2.0服务向Web应用返回访问令牌（access\_token）。

7.  Web应用通过获取的访问令牌（access\_token）向阿里云发起访问API的请求。

    **说明：** 由于访问令牌（access\_token）可以代表用户身份，因此应用可以访问当前用户的资源。


## 获取访问令牌

1.  Web应用通过浏览器将用户重定向到阿里云OAuth 2.0服务从而获取授权码。

    授权码的请求地址：`https://signin.aliyun.com/oauth2/v1/auth`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |client\_id|是|应用ID。|
    |redirect\_uri|是|创建应用的重定向URI之一。|
    |response\_type|是|返回类型。根据OAuth 2.0协议，目前支持设置此参数的取值为code。|
    |scope|否|空格分隔的OAuth范围列表。如不指定此参数取值，则默认为应用的全部OAuth范围。|
    |access\_type|否|应用的访问类型。取值分为两种类型：     -   online：应用不需要离线刷新访问令牌。
    -   offline：针对离线访问类型的请求，会发放刷新令牌，应用可以根据需求持续刷新访问令牌。
默认取值为online。 |
    |state|否|应用通过state 参数实现多种目的，例如：状态保持、作为nonce使用从而减少CSRF威胁等。state如果设置为任意字符串，阿里云OAuth2.0服务会将请求中的state参数及取值原样放到返回参数中以供后续使用。|
    |prompt|否|该参数用于指定服务器是否需要提示用户进行授权操作。如果指定，会强制要求用户进行授权，即使该阿里云账号已经做过授权，也需要重新授权。如果不指定，则只在该阿里云账号第一次使用该应用时要求授权。

取值：`admin_consent`，表示服务端会在向客户端返回信息之前展示授权页面。 |

    请求示例

    ```
    https://signin.aliyun.com/oauth2/v1/auth?
    client_id=123****
    redirect_uri=https%3A%2F%2Fyourwebapp.com%2Fauthcallback%2F&
    response_type=code&
    scope=openid%20%2Facs%2Fccc&
    access_type=offline&
    state=123456****
    ```

    返回示例

    ```
    GET HTTP/1.1 302 Found
    Location: https://yourwebapp.com/authcallback/?code=ABAFDGDFXYZW888&state=123456****
    ```

2.  Web应用使用授权码向阿里云OAuth 2.0服务申请代表用户身份的令牌。

    换取访问令牌的请求地址：`https://oauth.aliyun.com/v1/token`。

    |参数名称|是否必选|描述|
    |:---|:---|:-|
    |code|是|初始请求中获取的授权码。|
    |client\_id|是|应用ID。|
    |redirect\_uri|是|初始请求中设置的参数。|
    |grant\_type|是|根据OAuth 2.0协议， 取值为authorization\_code。|
    |client\_secret|否|应用密钥，用作换取访问令牌时鉴定应用身份的密码。|

    请求示例

    ```
    POST /v1/token HTTP/1.1
    Host: oauth.aliyun.com
    Content-Type: application/x-www-form-urlencoded
    code=ABAFDGDFXYZW888&
    client_id=123****
    client_secret=`your_client_secret`&
    redirect_uri=https://yourwebapp.com/authcallback/&
    grant_type=authorization_code
    ```

    |参数名称|描述|
    |:---|:-|
    |access\_token|访问令牌。访问令牌可以代表用户身份，应用使用此访问令牌来访问阿里云API。应用不需要理解访问令牌的含义，直接使用即可。|
    |expires\_in|访问令牌的剩余有效时间，单位为秒。|
    |token\_type|访问令牌的类型。取值为Bearer。|
    |id\_token|身份令牌。身份令牌为OAuth签名的JWT（JSON Web Token）。如果初始请求的scope参数包含了openid，则返回身份令牌。|
    |refresh\_token|刷新令牌。如果初始请求时应用的访问类型为offline，则返回刷新令牌。|

    返回示例

    ```
    {
      "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
      "token_type": "Bearer",
      "expires_in": 3600,
      "refresh_token": "Ccx63VVeTn2dxV7ovXXfLtAqLLERA****",
      "id_token": "eyJhbGciOiJIUzI1****"
    }
    ```


## 获取新的访问令牌

换取访问令牌的请求地址：`https://oauth.aliyun.com/v1/token`。

|参数名称|是否必选|描述|
|:---|:---|:-|
|refresh\_token|是|用授权码换取访问令牌时获得的刷新令牌。|
|client\_id|是|应用ID。|
|grant\_type|是|根据OAuth 2.0协议， 取值为refresh\_token。|
|client\_secret|否|应用密钥，用作换取访问令牌时鉴定应用身份的密码。|

请求示例

```
POST /v1/token HTTP/1.1
Host: oauth.aliyun.com
Content-Type: application/x-www-form-urlencoded
refresh_token=Ccx63VVeTn2dxV7ovXXfLtAqLLERAH1Bc&
client_id=123****
client_secret=`your_client_secret`&
grant_type=refresh_token
```

|参数名称|描述|
|:---|:-|
|access\_token|新的访问令牌。应用可以使用新的访问令牌来访问阿里云API。|
|expires\_in|访问令牌的剩余有效时间，单位为秒。|
|token\_type|访问令牌的类型。取值为Bearer。|

返回示例

```
{
  "access_token": "eyJraWQiOiJrMTIzNCIsImVu****",
  "token_type": "Bearer",
  "expires_in": 3600,
}
```

## 撤销刷新令牌

Web应用获取了刷新令牌后，在用户退出登录应用或用户将自己的账号从应用中移除时，必须撤销刷新令牌。

撤销刷新令牌的请求地址：`https://oauth.aliyun.com/v1/revoke`。

|参数名称|是否必选|描述|
|:---|:---|:-|
|token|是|需要撤销的刷新令牌。|
|client\_id|是|应用ID。|
|client\_secret|否|应用密钥。|

