# GetApplication

调用GetApplication查询应用的配置信息。

本文将提供一个示例，查询应用`472457090344041****`的配置信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=GetApplication&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetApplication|要执行的操作。取值：**GetApplication**。 |
|AppId|String|是|472457090344041\*\*\*\*|应用ID。 |

关于公共请求参数的详情，请参见[公共参数](~~187377~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6616F09B-2768-4C11-8866-A8EE4C4A583E|请求ID。 |
|Application|Object| |应用信息。 |
|DisplayName|String|myapp|应用的显示名称。 |
|AccessTokenValidity|Integer|3600|访问令牌有效期。单位：秒。 |
|SecretRequired|Boolean|true|是否需要应用密钥。 |
|AccountId|String|177242285274\*\*\*\*|应用所属的阿里云账号ID。 |
|CreateDate|String|2020-10-23T08:06:57Z|创建时间。 |
|AppName|String|myapp|应用名称。 |
|RedirectUris|Array of String|https://www.example.com|回调地址。 |
|UpdateDate|String|2020-10-23T08:06:57Z|更新时间。 |
|DelegatedScope|Object| |应用权限范围信息。 |
|PredefinedScopes|Array of PredefinedScope| |应用权限范围信息。 |
|PredefinedScope| | | |
|Description|String|用于获取用户的OpenID（默认权限范围，不可移除）|范围描述。 |
|Name|String|openid|范围名称。 |
|AppId|String|472457090344041\*\*\*\*|应用ID。 |
|RefreshTokenValidity|Integer|7776000|刷新令牌有效期。单位：秒。 |
|IsMultiTenant|Boolean|true|是否允许被其他账号安装。 |
|AppType|String|WebApp|应用类型。取值：

 -   WebApp：指基于浏览器交互的网络应用。
-   NativeApp：指操作系统中运行的本地应用，主要为运行在桌面操作系统或移动操作系统中的应用。
-   ServerApp：指直接访问阿里云服务，而无需依赖用户登录的应用，目前仅支持基于SCIM协议的用户同步应用。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=GetApplication
&AppId=472457090344041****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<GetApplicationResponse>
        <RequestId>6616F09B-2768-4C11-8866-A8EE4C4A583E</RequestId>
        <Application>
                <AccountId>177242285274****</AccountId>
                <SecretRequired>true</SecretRequired>
                <IsMultiTenant>true</IsMultiTenant>
                <CreateDate>2020-10-23T08:06:57Z</CreateDate>
                <AppName>myapp</AppName>
                <UpdateDate>2020-10-23T08:06:57Z</UpdateDate>
                <DelegatedScope>
                        <PredefinedScopes>
                                <PredefinedScope>
                                        <Description>用于获取用户的OpenID（默认权限范围，不可移除）</Description>
                                        <Name>openid</Name>
                                </PredefinedScope>
                        </PredefinedScopes>
                </DelegatedScope>
                <AppId>472457090344041****</AppId>
                <DisplayName>myapp</DisplayName>
                <AccessTokenValidity>3600</AccessTokenValidity>
                <RedirectUris>
                        <RedirectUri>https://www.example.com</RedirectUri>
                </RedirectUris>
                <RefreshTokenValidity>7776000</RefreshTokenValidity>
                <AppType>WebApp</AppType>
        </Application>
</GetApplicationResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "6616F09B-2768-4C11-8866-A8EE4C4A583E",
  "Application" : {
    "AccountId" : "177242285274****",
    "SecretRequired" : true,
    "IsMultiTenant" : true,
    "CreateDate" : "2020-10-23T08:06:57Z",
    "AppName" : "myapp",
    "UpdateDate" : "2020-10-23T08:06:57Z",
    "DelegatedScope" : {
      "PredefinedScopes" : {
        "PredefinedScope" : [ {
          "Description" : "用于获取用户的OpenID（默认权限范围，不可移除）",
          "Name" : "openid"
        } ]
      }
    },
    "AppId" : "472457090344041****",
    "DisplayName" : "myapp",
    "AccessTokenValidity" : 3600,
    "RedirectUris" : {
      "RedirectUri" : [ "https://www.example.com" ]
    },
    "RefreshTokenValidity" : 7776000,
    "AppType" : "WebApp"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

