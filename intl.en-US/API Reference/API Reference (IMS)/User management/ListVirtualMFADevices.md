# ListVirtualMFADevices

Queries multi-factor authentication \(MFA\) devices.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=ListVirtualMFADevices&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListVirtualMFADevices|The operation that you want to perform. Set the value to ListVirtualMFADevices. |
|Marker|String|No|EXAMPLE|The `marker`. If part of a previous response is truncated, you can use this parameter to obtain the truncated part. |
|MaxItems|Integer|No|100|The number of entries to return. If a response is truncated because it reaches the value of `MaxItems`, the value of `IsTruncated` will be `true`.

Valid values: 1 to 100. Default value: 100. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|true|Indicates whether the response is truncated. Valid values:

-   true
-   false |
|Marker|String|EXAMPLE|The `marker`. This parameter is returned only if the value of `IsTruncated` is `true`. If the parameter is returned, you can call this operation again and set this parameter to obtain the truncated part. |
|RequestId|String|32272612-DF82-485E-8BA9-AFA4E0C3D0BA|The ID of the request. |
|VirtualMFADevices|Array of VirtualMFADevice| |The information of the MFA device. |
|VirtualMFADevice| | | |
|ActivateDate|String|2020-10-16T06:02:09Z|The time when the MFA device was activated. |
|SerialNumber|String|acs:ram::177242285274\*\*\*\*:mfa/test|The serial number of the MFA device. |
|User|Struct| |The information of the RAM user that has an MFA device bound. |
|DisplayName|String|test|The display name of the RAM user. |
|UserId|String|20732900249392\*\*\*\*|The ID of the RAM user. |
|UserPrincipalName|String|test@177242285274\*\*\*\*.onaliyun.com|The logon name of the RAM user. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=ListVirtualMFADevices
&Marker=EXAMPLE
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

