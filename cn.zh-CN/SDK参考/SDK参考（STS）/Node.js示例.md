# Node.js示例

本文简要介绍了Node.js SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于STS API的详情，请参见[什么是STS](/cn.zh-CN/API参考/API 参考（STS）/什么是STS.md)。
-   关于STS的接入地址，请参见[接入地址](/cn.zh-CN/API参考/API 参考（STS）/接入地址.md)。

## Node.js SDK的安装方法

您可以通过npm安装Node.js SDK，并写入package.json依赖项，命令如下：

`$ npm install @alicloud/pop-core --save`

具体的安装方法，请参见[快速开始]()。

Node.js SDK安装包下载地址如下：

-   [Node.js SDK](https://github.com/aliyun/openapi-core-nodejs-sdk)
-   [STS SDK](https://github.com/aliyun/nodejs-sts-sdk)

## Node.js SDK示例

下面为您提供AssumeRole API的Node.js SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)调试并获取示例代码。

```
const Core = require('@alicloud/pop-core');

//构建一个阿里云客户端, 用于发起请求。
//构建阿里云客户端时，需要设置AccessKey ID和AccessKey Secret。
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

//设置参数。
var params = {
  "RegionId": "cn-hangzhou",
  "RoleArn": "<RoleARN>",
  "RoleSessionName": "<RoleSessionName>"
}

var requestOption = {
  method: 'POST'
};

//发起请求，并得到响应。
client.request('AssumeRole', params, requestOption).then((result) => {
  console.log(JSON.stringify(result));
}, (ex) => {
  console.log(ex);
})           
```

