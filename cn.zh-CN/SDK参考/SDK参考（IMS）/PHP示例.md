# PHP示例

本文简要介绍了PHP SDK的安装方法，并提供了示例代码。

## 背景信息

关于IMS API的详情，请参见[API概览](/cn.zh-CN/API参考/API 参考（IMS）/API概览.md)。

## PHP SDK的安装方法

请先安装Composer，然后执行如下命令，安装PHP SDK：

```
composer require alibabacloud/ims-20190815
```

PHP SDK安装包下载地址：[Alibaba Cloud IMS SDK for PHP](https://github.com/alibabacloud-sdk-php/ims-20190815)。

## PHP SDK示例

下面为您提供[CreateUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateUser.md) API的PHP SDK示例代码。

```
<?php

// This file is auto-generated, don't edit it. Thanks.
namespace Alibabacloud\Sample\ImsUser;

use AlibabaCloud\SDK\Ims\V20190815\Ims;
use AlibabaCloud\Tea\Utils\Utils;
use AlibabaCloud\Tea\Tea;
use \Exception;
use AlibabaCloud\Tea\Exception\TeaError;

use AlibabaCloud\Tea\Rpc\Rpc\Config;
use AlibabaCloud\SDK\Ims\V20190815\Models\CreateUserRequest;
use AlibabaCloud\SDK\Ims\V20190815\Models\CreateUserResponse;
use AlibabaCloud\SDK\Ims\V20190815\Models\GetDefaultDomainRequest;
use AlibabaCloud\SDK\Ims\V20190815\Models\GetDefaultDomainResponse;
use AlibabaCloud\SDK\Ims\V20190815\Models\GetUserRequest;
use AlibabaCloud\SDK\Ims\V20190815\Models\GetUserResponse;

class Client {

    /**
     * Initialization  初始化公共请求参数
     * @return Ims
     */
    public static function Initialization(){
        $config = new Config([]);
        // 您的AccessKey ID
        $config->accessKeyId = "<accessKeyId>";
        // 您的AccessKey Secret
        $config->accessKeySecret = "<accessKeySecret>";
        // 您的地域ID
        $config->regionId = "<regionId>";
        return new Ims($config);
    }

    /**
     * CreateUser  创建RAM用户
     * @param Ims $client
     * @param string $userPrincipalName
     * @param string $displayName
     * @return void
     */
    public static function CreateUser($client, $userPrincipalName, $displayName){
        $req = new CreateUserRequest([]);
        // RAM用户的登录名称。格式为<username>@<AccountAlias>.onaliyun.com，其中<username>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
        $req->userPrincipalName = $userPrincipalName;
        // RAM用户的显示名称
        $req->displayName = $displayName;
        $resp = $client->createUser($req);
        echo "--------------------创建RAM用户--------------------";
        echo Utils::toJSONString(Tea::merge($resp));
    }

    /**
     * GetDefaultDomain  获取阿里云账号默认域名
     * @param Ims $client
     * @return string
     */
    public static function GetDefaultDomain($client){
        $req = new GetDefaultDomainRequest([]);
        $resp = $client->getDefaultDomain($req);
        echo "--------------------获取阿里云账号默认域名--------------------";
        echo Utils::toJSONString(Tea::merge($resp));
        return $resp->defaultDomainName;
    }

    /**
     * GetUser  查询RAM用户的详细信息
     * @param Ims $client
     * @param string $userPrincipalName
     * @return void
     */
    public static function GetUser($client, $userPrincipalName){
        $req = new GetUserRequest([]);
        // RAM用户的登录名称
        $req->userPrincipalName = $userPrincipalName;
        $resp = $client->getUser($req);
        echo "--------------------查询RAM用户的详细信息--------------------";
        echo Utils::toJSONString(Tea::merge($resp));
    }

    /**
     * @param string[] $args
     * @return void
     */
    public static function main($args){
        try {
            $client = self::Initialization();
            $defaultDomain = self::GetDefaultDomain($client);
            $userName = "<UserName>";
            // RAM用户的登录名称。格式为<username>@<AccountAlias>.onaliyun.com，其中<username>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
            $userPrincipalName = "" . $userName . "@" . $defaultDomain . "";
            // RAM用户的显示名称
            $displayName = "<displayName>";
            self::CreateUser($client, $userPrincipalName, $displayName);
            self::GetUser($client, $userPrincipalName);
        }
        catch (Exception $error) {
            if (!($error instanceof TeaError)) {
                $error = new TeaError([], $error->getMessage(), $error->getCode(), $error);
            }
            echo $error->message;
        }
    }
}
$path = __DIR__ . \DIRECTORY_SEPARATOR . '..' . \DIRECTORY_SEPARATOR . 'vendor' . \DIRECTORY_SEPARATOR . 'autoload.php';
if (file_exists($path)) {
    require_once $path;
}
Client::main(array_slice($argv, 1));
```

