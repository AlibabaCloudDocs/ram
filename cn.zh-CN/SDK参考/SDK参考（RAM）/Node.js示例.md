# Node.js示例

本文简要介绍了Node.js SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI Explorer](https://api.aliyun.com/)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于RAM API的详情，请参见[RAM API](/cn.zh-CN/API参考（RAM）/API概览.md)。

## Node.js SDK的安装方法

您可以通过npm安装Node.js SDK，并写入package.json依赖项，命令如下：

`$ npm install @alicloud/pop-core --save`

具体的安装方法，请参见[快速开始]()。

Node.js SDK安装包下载地址如下：

-   [Node.js SDK](https://www.npmjs.com/package/@alicloud/pop-core)
-   [RAM SDK](https://www.npmjs.com/package/@alicloud/ram-2015-05-01)

## Node.js SDK示例

下面为您提供CreateUser API的Node.js SDK示例代码。关于其他API，请访问[OpenAPI Explorer](https://api.aliyun.com/)调试并获取示例代码。

```
const Core = require('@alicloud/pop-core');
//构建一个阿里云客户端, 用于发起请求。
//构建阿里云客户端时，需要设置AccessKey ID和AccessKey Secret。
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://ram.aliyuncs.com',
  apiVersion: '2015-05-01'
});
//设置参数。
var params = {
  "RegionId": "cn-hangzhou",
  "UserName": "<UserName>"
}

var requestOption = {
  method: 'POST'
};
//发起请求，并得到响应。
client.request('CreateUser', params, requestOption).then((result) => {
  console.log(JSON.stringify(result));
}, (ex) => {
  console.log(ex);
})
```

