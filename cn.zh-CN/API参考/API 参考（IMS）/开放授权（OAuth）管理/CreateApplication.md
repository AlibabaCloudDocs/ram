# CreateApplication

调用CreateApplication创建应用。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=CreateApplication&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateApplication|要执行的操作。取值：CreateApplication。 |
|AppType|String|是|WebApp|应用类型。取值：

 -   WebApp：指基于浏览器交互的网络应用。
-   NativeApp：指操作系统中运行的本地应用，主要为运行在桌面操作系统或移动操作系统中的应用。
-   ServerApp：指直接访问阿里云服务，而无需依赖用户登录的应用，目前仅支持基于SCIM协议的用户同步应用。 |
|DisplayName|String|是|myapp|应用的显示名称。

 最大长度为24个字符。 |
|AppName|String|是|myapp|应用名称。

 最大长度为64 个字符，允许输入英文字母、数字、英文句点（.）、下划线（\_）或中划线（-）。 |
|SecretRequired|Boolean|否|true|是否需要应用密钥。取值：

 -   true
-   false

 **说明：**

-   对于WebApp和ServerApp类型的应用，该值会被强制设置为true，不支持修改。
-   对于NativeApp类型的应用，可以设置为true或false，如不设置，默认为false。由于此类应用往往运行在非可信环境，无法有效保护应用密钥，因此建议您如无明确需要，不要设置为true。更多信息，请参见[Native应用登录阿里云](~~93697~~)。 |
|AccessTokenValidity|Integer|否|3600|访问令牌有效期。

 取值范围：900~10800。单位：秒。

 默认值：3600。 |
|RefreshTokenValidity|Integer|否|2592000|刷新令牌有效期。

 取值范围：7200~31536000。单位：秒。

 默认值：

 -   对于NativeApp和ServerApp类型的应用，如果该值为空，则默认为2592000秒（即30天）。
-   对于WebApp类型的应用，如果该值为空，则默认为7776000秒（即90天）。 |
|PredefinedScopes|String|否|aliuid|应用权限范围。

 关于应用权限范围的取值和描述，请参见[OAuth范围](~~93693~~)。您也可以调用[ListPredefinedScopes](~~187206~~)获取不同应用类型支持的应用权限范围。

 输入多个应用权限范围时，以英文分号（;）分隔。 |
|IsMultiTenant|Boolean|否|false|是否允许被其他账号安装。取值：

 -   true：对于NativeApp和ServerApp类型的应用，如果该值为空，则默认为true。
-   false：对于WebApp类型的应用，如果该值为空，则默认为false。 |
|RedirectUris|String|否|https://www.example.com|回调地址。

 输入多个时，以英文分号（;）分隔。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Application|Struct| |应用信息。 |
|AccessTokenValidity|Integer|3600|访问令牌有效期。单位：秒。 |
|AccountId|String|177242285274\*\*\*\*|应用所属的阿里云账号ID。 |
|AppId|String|472457090344041\*\*\*\*|应用ID。 |
|AppName|String|myapp|应用名称。 |
|AppType|String|WebApp|应用类型。 |
|CreateDate|String|2020-10-23T08:06:57Z|创建时间。 |
|DelegatedScope|Struct| |应用权限范围信息。 |
|PredefinedScopes|Array of PredefinedScope| |应用权限范围信息。 |
|PredefinedScope| | | |
|Description|String|用于获取用户的OpenID（默认权限范围，不可移除）|范围描述。 |
|Name|String|openid|范围名称。 |
|DisplayName|String|myapp|应用的显示名称。 |
|IsMultiTenant|Boolean|true|是否允许被其他账号安装。 |
|RedirectUris|List|https://www.example.com|回调地址。 |
|RefreshTokenValidity|Integer|7776000|刷新令牌有效期。单位：秒。 |
|SecretRequired|Boolean|true|是否需要应用密钥。 |
|UpdateDate|String|2020-10-23T08:06:57Z|更新时间。 |
|RequestId|String|6616F09B-2768-4C11-8866-A8EE4C4A583E|请求ID。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=CreateApplication
&AppType=WebApp
&AppName=myapp
&DisplayName=myapp
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateApplicationResponse>
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
</CreateApplicationResponse>
```

`JSON` 格式

```
{
  "RequestId": "6616F09B-2768-4C11-8866-A8EE4C4A583E",
  "Application": {
    "AccountId": "177242285274****",
    "SecretRequired": true,
    "IsMultiTenant": true,
    "CreateDate": "2020-10-23T08:06:57Z",
    "AppName": "myapp",
    "UpdateDate": "2020-10-23T08:06:57Z",
    "DelegatedScope": {
      "PredefinedScopes": {
        "PredefinedScope": [
          {
            "Description": "用于获取用户的OpenID（默认权限范围，不可移除）",
            "Name": "openid"
          }
        ]
      }
    },
    "AppId": "472457090344041****",
    "DisplayName": "myapp",
    "AccessTokenValidity": 3600,
    "RedirectUris": {
      "RedirectUri": [
        "https://www.example.com"
      ]
    },
    "RefreshTokenValidity": 7776000,
    "AppType": "WebApp"
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

