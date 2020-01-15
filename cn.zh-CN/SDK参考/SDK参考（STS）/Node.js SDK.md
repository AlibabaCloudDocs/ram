# Node.js SDK {#concept_fvb_xzy_xdb .concept}

本文简要介绍了Node.js SDK的安装并提供一个简单的操作示例。

## Node.js SDK的安装 {#section_egk_sbz_xdb .section}

通过npm安装Node.js SDK：`npm install -S @alicloud/pop-core`。

## Node.js SDK示例 {#section_c4w_0ax_p6c .section}

``` {#codeblock_vxy_igi_mt4}
/*
  Usage: npm install -S @alicloud/pop-core
  powered by alinode (http://alinode.aliyun.com/)
*/

const Core = require('@alicloud/pop-core');
// 构建一个阿里云client, 用于发起请求
// 构建阿里云client时需要设置AccessKey ID和AccessKey Secret
var client = new Core({
  accessKeyId: '<accessKeyId>',
  accessKeySecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

//设置参数，指定角色ARN
var params = {
  'RoleArn': '<role-arn>',
  'RoleSessionName': 'session-name'
};

//构建AssumeRole请求
client.request('AssumeRole', params).then((result) => {
  console.log(result);
}, (ex) => {
  console.log(ex);
})
```

**说明：** 

-   STS各区域的endpoint，请参见[接入地址](../../../../cn.zh-CN/API 参考（STS）/调用方式/接入地址.md#)。
-   AssumeRole接口相关信息，请参见[AssumeRole](../../../../cn.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

