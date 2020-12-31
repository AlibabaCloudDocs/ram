# IMS SDK for PHP

This topic describes how to install Identity Management Service \(IMS\) SDK for PHP and provides an example on how to use IMS SDK for PHP.

## Background information

For more information about IMS API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md).

## Install IMS SDK for PHP

Install Composer. Then, run the following command to install IMS SDK for PHP:

```
composer require alibabacloud/ims-20190815
```

To download the installation package of IMS SDK for PHP, click [Alibaba Cloud IMS SDK for PHP](https://github.com/alibabacloud-sdk-php/ims-20190815).

## Sample code

The following code provides an example on how to call the [CreateUser](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateUser.md) API operation by using IMS SDK for PHP.

```
<? php

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
     * Initialization  Initializes common request parameters.
     * @return Ims
     */
    public static function Initialization(){
        $config = new Config([]);
        // The AccessKey ID.
        $config->accessKeyId = "<accessKeyId>";
        // The AccessKey secret.
        $config->accessKeySecret = "<accessKeySecret>";
        // The ID of the region.
        $config->regionId = "<regionId>";
        return new Ims($config);
    }

    /**
     * CreateUser  Creates a RAM user.
     * @param Ims $client
     * @param string $userPrincipalName
     * @param string $displayName
     * @return void
     */
    public static function CreateUser($client, $userPrincipalName, $displayName){
        $req = new CreateUserRequest([]);
        // The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
        $req->userPrincipalName = $userPrincipalName;
        // The display name of the RAM user.
        $req->displayName = $displayName;
        $resp = $client->createUser($req);
        echo "-------------------- Creates a RAM user --------------------";
        echo Utils::toJSONString(Tea::merge($resp));
    }

    /**
     * GetDefaultDomain  Obtains the default domain name of your Alibaba Cloud account.
     * @param Ims $client
     * @return string
     */
    public static function GetDefaultDomain($client){
        $req = new GetDefaultDomainRequest([]);
        $resp = $client->getDefaultDomain($req);
        echo "-------------------- Obtains the default domain name of your Alibaba Cloud account --------------------";
        echo Utils::toJSONString(Tea::merge($resp));
        return $resp->defaultDomainName;
    }

    /**
     * GetUser  Queries detailed information about a RAM user.
     * @param Ims $client
     * @param string $userPrincipalName
     * @return void
     */
    public static function GetUser($client, $userPrincipalName){
        $req = new GetUserRequest([]);
        // The logon name of the RAM user.
        $req->userPrincipalName = $userPrincipalName;
        $resp = $client->getUser($req);
        echo "-------------------- Queries detailed information about a RAM user. --------------------";
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
            // The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
            $userPrincipalName = "" . $userName . "@" . $defaultDomain . "";
            // The display name of the RAM user.
            $displayName = "<displayName>";
            self::CreateUser($client, $userPrincipalName, $displayName);
            self::GetUser($client, $userPrincipalName);
        }
        catch (Exception $error) {
            if (!( $error instanceof TeaError)) {
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

