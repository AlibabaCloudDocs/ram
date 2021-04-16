# STS SDK for Node.js

This topic describes how to install STS SDK for Node.js and provides an example about how to use the SDK for Node.js.

## Background information

-   Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see .
-   For information about endpoints to access STS, see .

## Install the SDK for Node.js

Run the following command to install the SDK for Node.js and add dependencies to the package.json file:

$ npm install @alicloud/pop-core --save

For more information, see .

You can download the installation packages of the SDK for Node.js from the following links:

-   Node.js SDK
-   STS SDK

## Sample code of the SDK for Node.js

The following sample code shows how to call the AssumeRole API operation by using the SDK for Node.js.You can visit OpenAPI Explorer to debug other API operations and obtain sample code.

```
const Core = require('@alicloud/pop-core');
 // Construct an Alibaba Cloud client to initiate requests.
// When you construct the client, specify your AccessKey ID and AccessKey secret.
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});
 // Specify request parameters.
var params = {
  "RegionId": "cn-hangzhou",
  "RoleArn": "<RoleARN>",
  "RoleSessionName": "<RoleSessionName>"
}
 var requestOption = {
  method: 'POST'
};
 // Initiate the request and obtain a response.
client.request('AssumeRole', params, requestOption).then((result) => {
  console.log(JSON.stringify(result));
}, (ex) => {
  console.log(ex);
})           
```

