# GetCredentialReport

Queries the content of a user credential report.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GetCredentialReport&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetCredentialReport|The operation that you want to perform. Set the value to GetCredentialReport. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Content|String|OVZWK4RMOVZW\*\*\*\*|The content of the user credential report.

 The report is Base64-encoded. After you decode the report, the credential report is in the CSV format. |
|GeneratedTime|String|2020-10-19T15:06:52Z|The time when the user credential report was generated. |
|RequestId|String|7A01826E-7601-44B0-B4DF-2B0C509836DE|The ID of the request. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GetCredentialReport
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetCredentialReportResponse>
	  <GeneratedTime>2020-10-19T15:06:52Z</GeneratedTime>
	  <RequestId>7A01826E-7601-44B0-B4DF-2B0C509836DE</RequestId>
	  <Content>OVZWK4RMOVZW****</Content>
</GetCredentialReportResponse>
```

`JSON` format

```
{
  "GeneratedTime": "2020-10-19T15:06:52Z",
  "RequestId": "7A01826E-7601-44B0-B4DF-2B0C509836DE",
  "Content": "OVZWK4RMOVZW****"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

