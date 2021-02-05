# Node.js示例

本文简要介绍了Node.js SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI开发者门户](https://next.api.aliyun.com)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于RAM API的详情，请参见[RAM API](/intl.zh-CN/API参考/API参考（RAM）/API概览.md)。

## Node.js SDK的安装方法

您可以通过npm安装Node.js SDK，并写入package.json依赖项，命令如下：

`npm i @alicloud/ram20150501 --save`

Node.js SDK安装包下载地址如下：

-   [Node.js SDK](https://www.npmjs.com/package/@alicloud/openapi-client)
-   [RAM SDK](https://www.npmjs.com/package/@alicloud/ram-2015-05-01)

## Node.js SDK示例

下面为您提供[CreateUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateUser.md) API的Node.js SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com)调试并获取示例代码。

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

//创建客户端。
const client = new Client(config);

//初始化请求。关于参数含义和设置方法，请参见API参考。
const createUserRequest = new CreateUserRequest({
  userName: "<UserName>"
});

//调用API。
const res = await client.createUser(createUserRequest);
console.log(res);
```

