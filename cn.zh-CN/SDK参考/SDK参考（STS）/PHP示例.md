# PHP示例

本文简要介绍了PHP SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI Explorer](https://api.aliyun.com/)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于STS API的详情，请参见[什么是STS](/cn.zh-CN/API 参考（STS）/什么是STS.md)。
-   关于STS的接入地址，请参见[接入地址](/cn.zh-CN/API 参考（STS）/接入地址.md)。

## PHP SDK的安装方法

PHP SDK的安装方法，请参见[快速开始]()。

PHP SDK安装包下载地址如下：

-   [PHP SDK](https://github.com/aliyun/openapi-sdk-php)
-   [STS SDK](https://github.com/aliyun/openapi-sdk-php/tree/master/src/Sts)

## PHP SDK示例

下面为您提供AssumeRole API的PHP SDK示例代码。关于其他API，请访问[OpenAPI Explorer](https://api.aliyun.com/)调试并获取示例代码。

```
<?php
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;

//构建一个阿里云客户端，用于发起请求。
//构建阿里云客户端时需要设置AccessKey ID和AccessKey Secret。
AlibabaCloud::accessKeyClient('<accessKeyId>', '<accessSecret>')
                        ->regionId('cn-hangzhou')
                        ->asDefaultClient();
//设置参数，发起请求。
try {
    $result = AlibabaCloud::rpc()
                          ->product('Sts')
                          // ->scheme('https') // https | http
                          ->version('2015-04-01')
                          ->action('AssumeRole')
                          ->method('POST')
                          ->host('sts.aliyuncs.com')
                          ->options([
                                        'query' => [
                                          'RegionId' => "cn-hangzhou",
                                          'RoleArn' => "<RoleArn>",
                                          'RoleSessionName' => "<RoleSessionName>",
                                        ],
                                    ])
                          ->request();
    print_r($result->toArray());
} catch (ClientException $e) {
    echo $e->getErrorMessage() . PHP_EOL;
} catch (ServerException $e) {
    echo $e->getErrorMessage() . PHP_EOL;
}
```

