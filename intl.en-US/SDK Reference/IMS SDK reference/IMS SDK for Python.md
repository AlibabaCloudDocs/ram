# IMS SDK for Python

This topic describes how to install Identity Management Service \(IMS\) SDK for Python and provides an example on how to use IMS SDK for Python.

## Background information

For more information about IMS API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md).

## Install IMS SDK for Python

Run the following command to install IMS SDK for Python:

```
pip install alibabacloud_ims20190815
```

To download the installation package of IMS SDK for Python, click [Alibaba Cloud IMS SDK for Python](https://pypi.org/project/alibabacloud-ims20190815).

## Sample code

The following code provides an example on how to call the [CreateUser](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateUser.md) API operation by using IMS SDK for Python.

```
# -*- coding: utf-8 -*-
# This file is auto-generated, don't edit it. Thanks.
import sys

from Tea.core import TeaCore

from alibabacloud_ims20190815.client import Client as ImsClient
from alibabacloud_tea_rpc import models as rpc_models
from alibabacloud_ims20190815 import models as ims_models
from alibabacloud_tea_util.client import Client as UtilClient


class Client(object):
    def __init__(self):
        pass

    @staticmethod
    def initialization():
        """
        Initialization  Initializes common request parameters.
        """
        config = rpc_models.Config()
        # The AccessKey ID.
        config.access_key_id = '<accessKeyId>'
        # The AccessKey secret.
        config.access_key_secret = '<accessKeySecret>'
        # The ID of the region.
        config.region_id = '<regionId>'
        return ImsClient(config)

    @staticmethod
    def create_user(client, user_principal_name, display_name):
        """
        CreateUser  Creates a RAM user.
        """
        req = ims_models.CreateUserRequest()
        # The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
        req.user_principal_name = user_principal_name
        # The display name of the RAM user.
        req.display_name = display_name
        resp = client.create_user(req)
        print('-------------------- Creates a RAM user.--------------------')
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))

    @staticmethod
    def get_default_domain(client):
        """
        GetDefaultDomain  Obtains the default domain name of your Alibaba Cloud account.
        """
        req = ims_models.GetDefaultDomainRequest()
        resp = client.get_default_domain(req)
        print('-------------------- Obtains the default domain name of your Alibaba Cloud account.--------------------')
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))
        return resp.default_domain_name

    @staticmethod
    def get_user(client, user_principal_name):
        """
        GetUser  Queries the information about a RAM user.
        """
        req = ims_models.GetUserRequest()
        # The logon name of the RAM user.
        req.user_principal_name = user_principal_name
        resp = client.get_user(req)
        print(-------------------- Queries the information about a RAM user. --------------------")
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))

    @staticmethod
    def main(args):
        try:
            client = Client.initialization()
            default_domain = Client.get_default_domain(client)
            user_name = '<UserName>'
            # The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
            user_principal_name = '%s@%s' % (user_name, default_domain)
            # The display name of the RAM user.
            display_name = '<displayName>'
            Client.create_user(client, user_principal_name, display_name)
            Client.get_user(client, user_principal_name)
        except Exception as error:
            print(error.message)


if __name__ == '__main__':
    Client.main(sys.argv[1:])
```

