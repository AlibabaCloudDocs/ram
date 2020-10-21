# Python示例

本文简要介绍了Python SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI Explorer](https://api.aliyun.com/)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于RAM API的详情，请参见[API概览](/intl.zh-CN/API参考（RAM）/API概览.md)。

## Python SDK的安装方法

Python SDK的安装方法，请参见[快速开始]()。

Python SDK安装包下载地址如下：

-   [Python SDK](https://pypi.python.org/pypi/aliyun-python-sdk-core)
-   [RAM SDK](https://pypi.python.org/pypi/aliyun-python-sdk-ram)

## Python SDK示例

下面为您提供CreateUser API的Python SDK示例代码。关于其他API，请访问[OpenAPI Explorer](https://api.aliyun.com/)调试并获取示例代码。

```
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkram.request.v20150501.CreateUserRequest import CreateUserRequest
#构建一个阿里云客户端，用于发起请求。
#构建阿里云客户端时需要设置AccessKey ID和AccessKey Secret。
client = AcsClient('<accessKeyId>', '<accessSecret>', 'cn-hangzhou')
#构建请求。
request = CreateUserRequest()
request.set_accept_format('json')
#设置参数。
request.set_UserName("<UserName>")
#发起请求，并得到响应。
response = client.do_action_with_exception(request)
# python2:  print(response)
print(str(response, encoding='utf-8'))
            
```

