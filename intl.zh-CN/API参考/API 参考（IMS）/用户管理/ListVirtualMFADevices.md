# ListVirtualMFADevices

调用ListVirtualMFADevices查询多因素认证设备列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ims&api=ListVirtualMFADevices&type=RPC&version=2019-08-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListVirtualMFADevices|要执行的操作。取值：ListVirtualMFADevices。 |
|Marker|String|否|EXAMPLE|当请求的返回结果被截断时，可以使用`Marker`获取从当前截断位置之后的内容。 |
|MaxItems|Integer|否|100|返回结果的条数。当返回结果达到`MaxItems`限制被截断时，返回参数`IsTruncated`将等于`true`。

 取值范围：1~100。默认值：100。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|IsTruncated|Boolean|true|请求返回结果是否被截断。取值：

 -   true
-   false |
|Marker|String|EXAMPLE|当`IsTruncated`为`true`时才有此参数，当返回`true`时，需要继续调用此接口，并且使用`Marker`获取截断后的内容 。 |
|RequestId|String|32272612-DF82-485E-8BA9-AFA4E0C3D0BA|请求ID。 |
|VirtualMFADevices|Array of VirtualMFADevice| |多因素认证设备信息。 |
|VirtualMFADevice| | | |
|ActivateDate|String|2020-10-16T06:02:09Z|激活时间。 |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/test|设备序列号。 |
|User|Struct| |绑定了多因素认证设备的RAM用户信息。 |
|DisplayName|String|test|RAM用户的显示名称。 |
|UserId|String|20732900249392\*\*\*\*|RAM用户ID。 |
|UserPrincipalName|String|test@177242285274\*\*\*\*.onaliyun.com|RAM用户的登录名称。 |

## 示例

请求示例

```
https://[Endpoint]/?Action=ListVirtualMFADevices
&Marker=EXAMPLE
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListVirtualMFADevicesResponse>
	  <VirtualMFADevices>
		    <VirtualMFADevice>
			      <User></User>
			      <SerialNumber>acs:ram::177242285274****:mfa/dev-01</SerialNumber>
		    </VirtualMFADevice>
		    <VirtualMFADevice>
			      <User>
				        <UserId>20732900249392****</UserId>
				        <DisplayName>test</DisplayName>
				        <UserPrincipalName>test@177242285274****.onaliyun.com</UserPrincipalName>
			      </User>
			      <SerialNumber>acs:ram::177242285274****:mfa/test</SerialNumber>
			      <ActivateDate>2020-10-16T06:02:09Z</ActivateDate>
		    </VirtualMFADevice>
	  </VirtualMFADevices>
	  <RequestId>32272612-DF82-485E-8BA9-AFA4E0C3D0BA</RequestId>
	  <IsTruncated>true</IsTruncated>
	  <Marker>EXAMPLE</Marker>
</ListVirtualMFADevicesResponse>
```

`JSON` 格式

```
{
  "VirtualMFADevices": {
    "VirtualMFADevice": [
      {
        "User": {},
        "SerialNumber": "acs:ram::177242285274****:mfa/dev-01"
      },
      {
        "User": {
          "UserId": "20732900249392****",
          "DisplayName": "test",
          "UserPrincipalName": "test@177242285274****.onaliyun.com"
        },
        "SerialNumber": "acs:ram::177242285274****:mfa/test",
        "ActivateDate": "2020-10-16T06:02:09Z"
      }
    ]
  },
  "RequestId": "32272612-DF82-485E-8BA9-AFA4E0C3D0BA",
  "IsTruncated": true,
  "Marker": "EXAMPLE"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Ims)查看更多错误码。

