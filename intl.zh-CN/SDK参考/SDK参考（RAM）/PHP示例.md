# PHP示例

本文简要介绍了PHP SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI开发者门户](https://next.api.aliyun.com)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于RAM API的详情，请参见[API概览](/intl.zh-CN/API参考/API参考（RAM）/API概览.md)。

## PHP SDK的安装方法

PHP SDK的安装方法，请参见[快速开始]()。

PHP SDK安装包下载地址如下：

-   [PHP SDK](https://github.com/aliyun/openapi-sdk-php)
-   [RAM SDK](https://github.com/aliyun/openapi-sdk-php/tree/master/src/Ram)

## PHP SDK示例

下面为您提供[CreateUser](/intl.zh-CN/API参考/API参考（RAM）/用户管理接口/CreateUser.md) API的PHP SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com)调试并获取示例代码。

```
<?php
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;

//构建一个阿里云客户端，用于发起请求。
//构建阿里云客户端时需要设置AccessKey ID和AccessKey Secret。
AlibabaCloud::accessKeyClient('<accessKeyId>', '<accessKeySecret>')
                        ->asDefaultClient();
//设置参数，发起请求。关于参数含义和设置方法，请参见API参考。
try {
    $result = AlibabaCloud::rpc()
                          ->product('Ram')
                          // ->scheme('https') // https | http
                          ->version('2015-05-01')
                          ->action('CreateUser')
                          ->method('POST')
                          ->host('ram.aliyuncs.com')
                          ->options([
                                        'query' => [
                                          'UserName' => "<UserName>",
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

