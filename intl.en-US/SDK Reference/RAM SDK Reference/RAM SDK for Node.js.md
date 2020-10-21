# RAM SDK for Node.js

This topic describes how to install RAM SDK for Node.js and provides an example about how to use the SDK for Node.js.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [RAM API](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Node.js

Run the following command to install the SDK for Node.js and add dependencies to the package.json file:

`$ npm install @alicloud/pop-core --save`

For information about how to install the SDK for Node.js, see [Get started]().

You can download the installation packages of the SDK for Node.js from the following links:

-   [Node.js SDK](https://www.npmjs.com/package/@alicloud/pop-core)
-   [RAM SDK](https://www.npmjs.com/package/@alicloud/ram-2015-05-01)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for Node.js. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
const Core = require('@alicloud/pop-core');
// Construct an Alibaba Cloud client that is used to initiate requests.
// When you construct the client, specify the AccessKey ID and AccessKey secret.
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://ram.aliyuncs.com',
  apiVersion: '2015-05-01'
});
// Configure parameters.
var params = {
  "RegionId": "cn-hangzhou",
  "UserName": "<UserName>"
}

var requestOption = {
  method: 'POST'
};
// Initiate a request and obtain a response.
client.request('CreateUser', params, requestOption).then((result) => {
  console.log(JSON.stringify(result));
}, (ex) => {
  console.log(ex);
})
```

