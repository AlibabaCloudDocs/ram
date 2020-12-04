# Python示例

本文简要介绍了Python SDK的安装方法，并提供了示例代码。

## 背景信息

关于IMS API的详情，请参见[API概览](/cn.zh-CN/API参考/API 参考（IMS）/API概览.md)。

## Python SDK的安装方法

执行以下命令，安装Python SDK：

```
pip install alibabacloud_ims20190815
```

Python SDK安装包下载地址：[Alibaba Cloud IMS SDK for Python](https://pypi.org/project/alibabacloud-ims20190815)。

## Python SDK示例

下面为您提供[CreateUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateUser.md) API的Python SDK示例代码。

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
        Initialization  初始化公共请求参数
        """
        config = rpc_models.Config()
        # 您的AccessKey ID
        config.access_key_id = '<accessKeyId>'
        # 您的AccessKey Secret
        config.access_key_secret = '<accessKeySecret>'
        # 您的地域ID
        config.region_id = '<regionId>'
        return ImsClient(config)

    @staticmethod
    def create_user(client, user_principal_name, display_name):
        """
        CreateUser  创建RAM用户
        """
        req = ims_models.CreateUserRequest()
        # RAM用户的登录名称。格式为<username>@<AccountAlias>.onaliyun.com，其中<username>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
        req.user_principal_name = user_principal_name
        # RAM用户的显示名称
        req.display_name = display_name
        resp = client.create_user(req)
        print('--------------------创建RAM用户--------------------')
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))

    @staticmethod
    def get_default_domain(client):
        """
        GetDefaultDomain  获取阿里云账号默认域名
        """
        req = ims_models.GetDefaultDomainRequest()
        resp = client.get_default_domain(req)
        print('--------------------获取阿里云账号默认域名--------------------')
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))
        return resp.default_domain_name

    @staticmethod
    def get_user(client, user_principal_name):
        """
        GetUser  查询RAM用户的详细信息
        """
        req = ims_models.GetUserRequest()
        # RAM用户的登录名称
        req.user_principal_name = user_principal_name
        resp = client.get_user(req)
        print('--------------------查询RAM用户的详细信息--------------------')
        print(UtilClient.to_jsonstring(TeaCore.to_map(resp)))

    @staticmethod
    def main(args):
        try:
            client = Client.initialization()
            default_domain = Client.get_default_domain(client)
            user_name = '<UserName>'
            # RAM用户的登录名称。格式为<username>@<AccountAlias>.onaliyun.com，其中<username>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
            user_principal_name = '%s@%s' % (user_name, default_domain)
            # RAM用户的显示名称
            display_name = '<displayName>'
            Client.create_user(client, user_principal_name, display_name)
            Client.get_user(client, user_principal_name)
        except Exception as error:
            print(error.message)


if __name__ == '__main__':
    Client.main(sys.argv[1:])
```

