# GenerateCredentialReport

Generates a user credential report.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ims&api=GenerateCredentialReport&type=RPC&version=2019-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GenerateCredentialReport|The operation that you want to perform. Set the value to GenerateCredentialReport. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|BBCCA90A-A1F0-4B16-B355-692247197805|The ID of the request. |
|State|String|STARTED|The generation status of the user credential report. Valid values:

 -   STARTED: The user credential report starts to generate.
-   INPROGRESS: The user credential report is being generated.
-   COMPLETED: The user credential report is generated. |

## Examples

Sample requests

```
https://[Endpoint]/?Action=GenerateCredentialReport
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GenerateCredentialReportResponse>
	  <RequestId>BBCCA90A-A1F0-4B16-B355-692247197805</RequestId>
	  <State>STARTED</State>
</GenerateCredentialReportResponse>
```

`JSON` format

```
{
  "RequestId": "BBCCA90A-A1F0-4B16-B355-692247197805",
  "State": "STARTED"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ims).

