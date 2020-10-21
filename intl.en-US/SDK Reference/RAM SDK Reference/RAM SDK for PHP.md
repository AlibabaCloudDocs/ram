# RAM SDK for PHP

This topic describes how to install RAM SDK for PHP and provides an example about how to use the SDK for PHP.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [List of operations by function](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for PHP

For information about how to install the SDK for PHP, see [Quick start]().

You can download the installation packages of the SDK for PHP from the following links:

-   [PHP SDK](https://github.com/aliyun/openapi-sdk-php)
-   [RAM SDK](https://github.com/aliyun/openapi-sdk-php/tree/master/src/Ram)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for PHP. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
<? php
use AlibabaCloud\Client\AlibabaCloud;
use AlibabaCloud\Client\Exception\ClientException;
use AlibabaCloud\Client\Exception\ServerException;

// Construct an Alibaba Cloud client that is used to initiate requests.
// When you construct the client, specify the AccessKey ID and AccessKey secret.
AlibabaCloud::accessKeyClient('<accessKeyId>', '<accessSecret>')
                        ->regionId('cn-hangzhou')
                        ->asDefaultClient();
// Configure parameters and initiate a request.
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
                                          'RegionId' => "cn-hangzhou",
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

