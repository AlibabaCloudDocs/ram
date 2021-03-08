# SDK for PHP

This topic describes how to install the SDK for PHP and provides an example of how to use the SDK for PHP.

## Background information

-   Alibaba Cloud provides [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about Resource Access Management \(RAM\) API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md).

## Install the SDK for PHP

For more information about how to install the SDK for PHP, see [Quick start]().

You can download the installation packages of the SDK for PHP from the following links:

-   [Alibaba Cloud SDK for PHP](https://github.com/aliyun/openapi-sdk-php)
-   [Alibaba Cloud RAM SDK for PHP](https://github.com/aliyun/openapi-sdk-php/tree/master/src/Ram)

## Example

The following code provides an example of how to call the [CreateUser](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/CreateUser.md) operation by using the SDK for PHP. You can use [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to debug other API operations and obtain sample code.

```
<? php
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;

// Construct an Alibaba Cloud client that is used to initiate requests.
// When you construct the client, specify your AccessKey ID and AccessKey secret.
AlibabaCloud::accessKeyClient('<accessKeyId>', '<accessKeySecret>')
                        ->asDefaultClient();
// Specify request parameters and initiate a request. For more information about the parameters, see API Reference.
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

