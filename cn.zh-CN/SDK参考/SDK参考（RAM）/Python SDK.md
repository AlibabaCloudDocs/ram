# Python SDK

本文简要介绍了Python SDK的安装方法，并提供了操作示例。

## Python SDK的安装方法

您可以使用pip或手动下载Python安装包后手动添加到项目中。

-   通过pip安装：`pip install aliyun-python-sdk-ram`。
-   Python SDK安装包下载地址：
    -   [aliyun-python-sdk-core：阿里云SDK基础包](https://pypi.python.org/pypi/aliyun-python-sdk-core)
    -   [aliyun-python-sdk-ram：访问控制（RAM）接口定义包](https://pypi.python.org/pypi/aliyun-python-sdk-ram)

## Python SDK示例

以下示例以Python SDK为例，说明如何创建RAM用户。

```
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore import client
from aliyunsdkram.request.v20150501 import CreateUserRequest

#构建一个阿里云client，用于发起请求, 构建时需设置Access Key ID和Access Key Secret
clt = client.AcsClient('<access-key-id>','<access-key-secret>')

#构建CreateUser请求
request = CreateUserRequest.CreateUserRequest()
#设置参数：UserName
request.set_UserName('alice')

#发起请求，并得到response
response = clt.do_action_with_exception(request)

print response
```

