# STS SDK for Node.js

This topic describes how to install STS SDK for Node.js and provides an example about how to use the SDK for Node.js.

## Background information

-   Alibaba Cloud provides [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Sts) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md).
-   For information about endpoints to access STS, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Install the SDK for Node.js

Run the following command to install the SDK for Node.js and add dependencies to the package.json file:

`$ npm install @alicloud/pop-core --save`

For information about how to install the SDK for Node.js, see [Get started]().

You can download the installation packages of the SDK for Node.js from the following links:

-   [Node.js SDK](https://github.com/aliyun/openapi-core-nodejs-sdk)
-   [STS SDK](https://github.com/aliyun/nodejs-sts-sdk)

## Example

The following code provides an example on how to call the AssumeRole API operation by using the SDK for Node.js. For information about other API operations, visit [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Sts), debug API operations, and obtain sample code.

```
const Core = require('@alicloud/pop-core');

// Construct an Alibaba Cloud client that is used to initiate requests.
// When you construct the client, specify the AccessKey ID and AccessKey secret.
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

// Configure parameters.
var params = {
  "RegionId": "cn-hangzhou",
  "RoleArn": "<RoleARN>",
  "RoleSessionName": "<RoleSessionName>"
}

var requestOption = {
  method: 'POST'
};

// Initiate a request and obtain a response.
client.request('AssumeRole', params, requestOption).then((result) => {
  console.log(JSON.stringify(result));
}, (ex) => {
  console.log(ex);
})           
```

