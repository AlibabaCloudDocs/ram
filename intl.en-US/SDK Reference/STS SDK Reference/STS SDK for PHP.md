# STS SDK for PHP

This topic describes how to install STS SDK for PHP and provides an example about how to use STS SDK for PHP.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://next.api.aliyun.com/api/Sts) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md)
-   For information about endpoints to access STS, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Install the SDK for PHP

For information about how to install the SDK for PHP, see [Quick start]().

You can download the installation packages of the SDK for PHP from the following links:

-   [PHP SDK](https://github.com/aliyun/openapi-sdk-php)
-   [STS SDK](https://github.com/aliyun/openapi-sdk-php/tree/master/src/Sts)

## Example

The following sample code shows how to call the AssumeRole API operation by using the SDK for PHP. You can use [OpenAPI Explorer](https://next.api.aliyun.com/api/Sts) to debug other API operations and obtain sample code.

```
<?php
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;

// Construct an Alibaba Cloud client to initiate requests.
// When you construct the client, specify your AccessKey ID and AccessKey secret.
AlibabaCloud::accessKeyClient('<accessKeyId>', '<accessSecret>')
                        ->regionId('cn-hangzhou')
                        ->asDefaultClient();
// Specify request parameters and initiate a request.
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

