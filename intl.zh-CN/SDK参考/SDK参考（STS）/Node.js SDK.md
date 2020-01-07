# Node.js SDK {#concept_fvb_xzy_xdb .concept}

本文简要介绍了 Node.js SDK 的安装并提供一个简单的操作示例。

## Node.js SDK 的安装 {#section_egk_sbz_xdb .section}

通过 npm 安装 Node.js SDK：

``` {#codeblock_rfl_xaf_zql}
npm install -S @alicloud/pop-core
```

## Node.js SDK 示例 {#section_c4w_0ax_p6c .section}

``` {#codeblock_vxy_igi_mt4}
/*
  Usage: npm install -S @alicloud/pop-core
  powered by alinode (http://alinode.aliyun.com/)
*/

const Core = require('@alicloud/pop-core');
// 构建一个阿里云 Client, 用于发起请求
// 构建阿里云 Client 时需要设置 access key ID 和 access key secret
var client = new Core({
  accessKeyId: '<accessKeyId>',
  AccessKeySecret: '<accessSecret>',
  endpoint: 'https://sts.aliyuncs.com',
  apiVersion: '2015-04-01'
});

//设置参数，指定角色 ARN
var params = {
  'RoleArn': '<role-arn>',
  'RoleSessionName': 'session-name'
};

//构建 AssumeRole 请求
client.request('AssumeRole', params).then((result) => {
  console.log(result);
}, (ex) => {
  console.log(ex);
})
```

**说明：** 

-   STS 各区域的 endpoint，请参考：[接入地址](../../../../intl.zh-CN/API 参考（STS）/调用方式/接入地址.md#)。
-   AssumeRole 接口相关信息，请参考：[AssumeRole](../../../../intl.zh-CN/API 参考（STS）/操作接口/AssumeRole.md#)。

