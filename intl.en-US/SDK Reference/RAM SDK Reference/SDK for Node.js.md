# SDK for Node.js

This topic describes how to install the SDK for Node.js and provides an example of how to use the SDK for Node.js.

## Background information

-   Alibaba Cloud provides [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about Resource Access Management \(RAM\) API operations, see [RAM API Reference](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Node.js

Run the following command to install the SDK for Node.js and add dependencies to the package.json file:

`npm i @alicloud/ram20150501 --save`

You can download the installation packages of the SDK for Node.js from the following links:

-   [Alibaba Cloud SDK for Node.js](https://www.npmjs.com/package/@alicloud/openapi-client)
-   [Alibaba Cloud RAM SDK for Node.js](https://www.npmjs.com/package/@alicloud/ram-2015-05-01)

## Example

The following code provides an example of how to call the [CreateUser](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/CreateUser.md) operation by using the SDK for Node.js. You can use [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to debug other API operations and obtain sample code.

```
'use strict';

const Client = require('@alicloud/ram20150501').default;
const { CreateUserRequest } = require('@alicloud/ram20150501');

const { Config } = require('@alicloud/openapi-client');

const config = new Config({
  endpoint: "<endpint>",
  accessKeyId: "<accessKeyId>",
  accessKeySecret: "<accessKeySecret>"
});

// Construct a client.
const client = new Client(config);

// Construct a request. For more information about the parameters, see API Reference.
const createUserRequest = new CreateUserRequest({
  userName: "<UserName>"
});

// Call an operation.
const res = await client.createUser(createUserRequest);
console.log(res);
```

