# ListApplications

调用ListApplications查询应用列表。

本文将提供一个示例，查询当前账号下的应用列表。返回结果显示，当前账号下只有一个名为`myapp`的应用。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListApplications&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListApplications|要执行的操作。取值：**ListApplications**。 |

关于公共请求参数的详情，请参见[公共参数](~~187377~~)。

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CE458B58-8C40-46F7-A9D4-CB85136B0C06|请求ID。 |
|Applications|Array of Application| |应用信息。 |
|Application| | | |
|DisplayName|String|myapp|应用的显示名称。 |
|AccessTokenValidity|Integer|3600|访问令牌有效期。单位：秒。 |
|SecretRequired|Boolean|true|是否需要应用密钥。 |
|AccountId|String|177242285274\*\*\*\*|应用所属的阿里云账号ID。 |
|CreateDate|String|2020-10-23T09:33:22Z|创建时间。 |
|AppName|String|myapp|应用名称。 |
|RedirectUris|Array of String|https://www.example.com|回调地址。 |
|UpdateDate|String|2020-10-23T09:33:22Z|更新时间。 |
|DelegatedScope|Object| |应用权限范围信息。 |
|PredefinedScopes|Array of PredefinedScope| |应用权限范围信息。 |
|PredefinedScope| | | |
|Description|String|用于获取用户的OpenID（默认权限范围，不可移除）|范围描述。 |
|Name|String|openid|范围名称。 |
|AppId|String|441442900344560\*\*\*\*|应用ID。 |
|RefreshTokenValidity|Integer|7776000|刷新令牌有效期。单位：秒。 |
|IsMultiTenant|Boolean|true|是否允许被其他账号安装。 |
|AppType|String|WebApp|应用类型。取值：

 -   WebApp：指基于浏览器交互的网络应用。
-   NativeApp：指操作系统中运行的本地应用，主要为运行在桌面操作系统或移动操作系统中的应用。
-   ServerApp：指直接访问阿里云服务，而无需依赖用户登录的应用，目前仅支持基于SCIM协议的用户同步应用。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListApplications
&<公共请求参数>
```

正常返回示例

`XML`格式

```
HTTP/1.1 200 OK
Content-Type:application/xml

<?xml version="1.0" encoding="UTF-8" ?>
<ListApplicationsResponse>
	<RequestId>CE458B58-8C40-46F7-A9D4-CB85136B0C06</RequestId>
	<Applications>
		<Application>
			<AccountId>177242285274****</AccountId>
			<SecretRequired>true</SecretRequired>
			<IsMultiTenant>true</IsMultiTenant>
			<CreateDate>2020-10-23T09:33:22Z</CreateDate>
			<AppName>myapp</AppName>
			<UpdateDate>2020-10-23T09:33:22Z</UpdateDate>
			<DelegatedScope>
				<PredefinedScopes>
					<PredefinedScope>
						<Description>用于获取用户的OpenID（默认权限范围，不可移除）</Description>
						<Name>openid</Name>
					</PredefinedScope>
					<PredefinedScope>
						<Description>用于获取阿里云UID</Description>
						<Name>aliuid</Name>
					</PredefinedScope>
				</PredefinedScopes>
			</DelegatedScope>
			<AppId>441442900344560****</AppId>
			<DisplayName>myapp</DisplayName>
			<AccessTokenValidity>3600</AccessTokenValidity>
			<RedirectUris>
				<RedirectUri>https://www.example.com</RedirectUri>
			</RedirectUris>
			<RefreshTokenValidity>7776000</RefreshTokenValidity>
			<AppType>WebApp</AppType>
		</Application>
	</Applications>
</ListApplicationsResponse>
```

`JSON`格式

```
HTTP/1.1 200 OK
Content-Type:application/json

{
  "RequestId" : "CE458B58-8C40-46F7-A9D4-CB85136B0C06",
  "Applications" : {
    "Application" : [ {
      "AccountId" : "177242285274****",
      "SecretRequired" : true,
      "IsMultiTenant" : true,
      "CreateDate" : "2020-10-23T09:33:22Z",
      "AppName" : "myapp",
      "UpdateDate" : "2020-10-23T09:33:22Z",
      "DelegatedScope" : {
        "PredefinedScopes" : {
          "PredefinedScope" : [ {
            "Description" : "用于获取用户的OpenID（默认权限范围，不可移除）",
            "Name" : "openid"
          }, {
            "Description" : "用于获取阿里云UID",
            "Name" : "aliuid"
          } ]
        }
      },
      "AppId" : "441442900344560****",
      "DisplayName" : "myapp",
      "AccessTokenValidity" : 3600,
      "RedirectUris" : {
        "RedirectUri" : [ "https://www.example.com" ]
      },
      "RefreshTokenValidity" : 7776000,
      "AppType" : "WebApp"
    } ]
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Ims)查看更多错误码。

