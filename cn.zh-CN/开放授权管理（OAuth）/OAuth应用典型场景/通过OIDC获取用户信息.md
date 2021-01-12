# 通过OIDC获取用户信息

OIDC（OpenID Connect）是建立在OAuth 2.0基础上的一个认证协议，本文为您介绍应用如何使用OIDC获取阿里云登录用户的信息。

应用获取用户登录信息首先需要创建应用，为应用提供恰当的名称、OAuth范围和回调地址等关键信息，并为应用生成应用密钥。详情请参见[创建应用](/cn.zh-CN/开放授权管理（OAuth）/管理OAuth应用/创建应用.md)。

## OIDC基本概念

|概念|说明|
|--|--|
|身份令牌|OIDC可以给应用下发代表登录用户的身份令牌。身份令牌用于获取姓名、登录名等用户信息，不能用于访问阿里云服务。|
|OIDC Discovery Endpoint|OIDC协议包含了不同的Endpoint用于不同的目的，Discovery Endpoint中包含OIDC协议所需要的所有配置信息，方便开发者使用。

**说明：** Discovery Endpoint是通过JSON文档来提供一系列键值，其中包含主要的提供者信息，例如：协议支持的响应类型、令牌颁发者的取值、身份令牌签名密钥的地址和签名算法等。

阿里云作为OIDC服务提供者，提供了一个Discovery Endpoint：`https://oauth.aliyun.com/.well-known/openid-configuration`来简化配置流程。

Discovery Endpoint包含的内容示例如下：

```
{
  "code_challenge_methods_supported": [
    "plain",
    "S256"
  ],
  "subject_types_supported": [
    "public"
  ],
  "response_types_supported": [
    "code"
  ],
  "issuer": "https://oauth.aliyun.com",
  "jwks_uri": "https://oauth.aliyun.com/v1/keys",
  "revocation_endpoint": "https://oauth.aliyun.com/v1/revoke",
  "token_endpoint": "https://oauth.aliyun.com/v1/token",
  "id_token_signing_alg_values_supported": [
    "RS256"
  ],
  "scopes_supported": [
    "openid",
    "aliuid",
    "profile"
  ],
  "authorization_endpoint": "https://signin.aliyun.com/oauth2/v1/auth"
}
``` |

## 基本流程

![IODC基本流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9324064951/p47437.png)

1.  用户通过浏览器登录应用。

2.  应用重定向到阿里云OIDC服务并将URL返回给浏览器。

    **说明：** 如果用户还未登录，则会进一步重定向到阿里云登录服务。

3.  用户通过浏览器登录阿里云OIDC服务并申请授权码。

4.  阿里云OIDC服务重定向到应用并返回授权码给浏览器。

5.  浏览器通过应用使用授权码向阿里云OIDC服务申请身份令牌。

    如何获取身份令牌的签名密钥，请参见[应用获取身份令牌签名密钥](#section_31e_m2z_uzf)。

6.  阿里云OIDC服务向应用返回身份令牌，应用通过身份令牌便可以获取用户信息。

    -   在身份令牌用于获取用户信息的场景下，由于身份令牌是由应用直接从OIDC服务获取的，因此应用不需要验证令牌的签名。

        用户信息返回示例请参见[用户信息返回示例](#section_at9_88y_ynv)。

    -   在身份令牌用于应用的各个不同模块之间通信的场景下，为保证信息安全，建议应用接受对身份令牌进行验证。

        如何验证身份令牌，请参见[验证身份令牌的JWT（JSON Web Token）签名](#section_bzg_o4n_qul)。


## 应用获取身份令牌签名密钥

请求示例

```
private List getSignPublicKey() {
  HttpResponse response = HttpClientUtils.doGet("https://oauth.aliyun.com/v1/keys");
  List rsaKeyList = new ArrayList();
  if (response.getCode() == 200 && response.isSuccess()) {
    String keys = JSON.parseObject(response.getData()).getString("keys");
    try {
      JSONArray publicKeyList = JSON.parseArray(keys);
      for (Object object : publicKeyList) {
        RSAKey rsaKey = RSAKey.parse(JSONObject.toJSONString(object));
        rsaKeyList.add(rsaKey);
      }
      return rsaKeyList;
    } catch (Exception e) {
      LOG.info(e.getMessage());
    }
  }
  LOG.info("GetSignPublicKey failed:{}", response.getData());
  throw new AuthenticationException(response.getData());
}                    
```

## 验证身份令牌的JWT（JSON Web Token）签名

阿里云颁发的身份令牌是带有签名的JWT，签名算法为JWS标准RS256。当应用请求获取用户信息时，阿里云需要对身份令牌进行验证，包含以下几个方面：

-   签名验证：通过OAuth服务公布的签名公钥，验证身份令牌的真实性和完整性。
-   有效期验证：检查令牌颁发时间和令牌过期时间的有效性。
-   检查令牌接收者：防止颁发给其他应用的身份令牌被传递给本应用。

请求示例

```
public boolean verifySign(SignedJWT signedJWT) {
  List publicKeyList = getSignPublicKey();
  RSAKey rsaKey = null;
  for (RSAKey key : publicKeyList) {
    if (signedJWT.getHeader().getKeyID().equals(key.getKeyID())) {
      rsaKey = key;
    }
  }
  if (rsaKey != null) {
    try {
      RSASSAVerifier verifier = new RSASSAVerifier(rsaKey.toRSAPublicKey());
      if (signedJWT.verify(verifier)) {
        return true;
      }
    } catch (Exception e) {
      LOG.info("Verify exception:{}", e.getMessage());
    }
  }
  throw new AuthenticationException("Can't verify signature for id token");
}
```

## 用户信息返回示例

|参数名称|描述|需要的 OAuth 范围|
|:---|:-|------------|
|alg|签名算法。|openid|
|kid|验证身份令牌签名使用的公钥，用户需要使用此公钥验证签名，防止身份令牌被篡改。|openid|

|参数名称|描述|需要的 OAuth 范围|
|:---|:-|------------|
|exp|令牌过期时间。|openid|
|sub|令牌主体，登录用户的 UID。|openid|
|aud|令牌接收者，OAuth应用ID。|openid|
|iss|令牌颁发者。取值为https://oauth.aliyun.com。|openid|
|iat|令牌颁发时间戳。|openid|
|name|登录用户的显示名称。|profile|
|upn|登录用户的UPN（User Principal Name）。RAM用户请求时才会返回该参数。|profile|
|login\_name|阿里云账号的登录名。阿里云账号请求时才会返回该参数。|profile|
|aid|登录用户所属的阿里云账号ID。|aliuid|
|uid|登录用户的阿里云账号ID。|aliuid|

返回示例

返回Header

```
{
  "alg": "RS256",
  "kid": "JC9wxzrhqJ0gtaCEt2QLUfevEUIwltFhui4O1bh****"
}
```

返回Body

为了阅读方便，这里展示的是未加密的身份令牌的返回。实际返回为加密的身份令牌，详情请参见[验证身份令牌的JWT（JSON Web Token）签名](#section_bzg_o4n_qul)。

-   阿里云账号请求时的返回Body

    ```
    {
      "exp": 1517539523,
      "sub": "123456789012****",
      "aud": "4567890123456****",
      "iss": "https://oauth.aliyun.com", //中国站
      "iat": 1517535923,
      "name": "alice", //登录用户的显示名称
      "login_name":"alice@example.com", //阿里云账号的登录名
      "aid": "123456789012****", //对应的阿里云账号ID
      "uid": "123456789012****", //登录用户的阿里云账号ID
    }
    ```

-   RAM用户请求时的返回Body

    ```
    {
      "exp": 1517539523,
      "sub": "123456789012****",
      "aud": "4567890123456****",
      "iss": "https://oauth.aliyun.com",
      "iat": 1517535923,
      "name": "alice", //登录用户的显示名称
      "upn": "alice@example.com", //RAM用户的登录名
      "aid": "123456789012****", //对应的阿里云账号ID
      "uid": "234567890123****", //登录用户的阿里云账号ID
    }
    ```


## 更多信息

除了直接获取身份令牌，您也可以在获取访问令牌后通过调用UserInfo接口获取用户信息，该接口必须使用访问令牌才能访问，返回信息不加密。

**说明：** OIDC场景下，即只有openid、aliuid和profile这几个范围的时候，也会返回访问令牌，此时的访问令牌只能用于调用UserInfo接口。

获取用户信息的请求地址：`https://oauth.aliyun.com/v1/userinfo`。

返回参数如下表所示：

|参数名称|描述|需要的 OAuth 范围|
|:---|:-|------------|
|sub|登录用户的UID。|openid|
|name|登录用户的显示名称。|profile|
|upn|登录用户的UPN（User Principal Name）。RAM用户请求时才会返回该参数。|profile|
|login\_name|阿里云账号的登录名。阿里云账号请求时才会返回该参数。|profile|
|aid|登录用户所属的阿里云账号ID。|aliuid|
|uid|登录用户的阿里云账号ID。|aliuid|

请求示例

```
GET v1/userinfo HTTP/1.1
Host: oauth.aliyun.com
Authorization: Bearer SlAV32hkKG 
```

返回Body

-   阿里云账号请求时的返回Body

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    {
      "sub": "123456789012****", 
      "name": "alice", //登录用户的显示名称
      "login_name":"alice@example.com", //阿里云账号的登录名
      "aid": "123456789012****", //对应的阿里云账号ID
      "uid": "123456789012****", //登录用户的阿里云账号ID
    }
    ```

-   RAM用户请求时的返回Body

    ```
    HTTP/1.1 200 OK
    Content-Type: application/json
    {
      "sub": "123456789012****", 
      "name": "alice", //登录用户的显示名称
      "upn": "alice@example.com", //RAM用户的登录名
      "aid": "123456789012****", //对应的阿里云账号ID
      "uid": "234567890123****", //登录用户的阿里云账号ID
    }
    ```


