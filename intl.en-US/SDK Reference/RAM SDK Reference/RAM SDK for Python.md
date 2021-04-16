# RAM SDK for Python

This topic describes how to install RAM SDK for Python and provides an example about how to use RAM SDK for Python.

## Background information

-   To use RAM SDK for Python, you must install the core library of Alibaba Cloud SDK for Python \(`aliyun-python-sdk-core`\) and the RAM SDK \(`aliyun-python-sdk-ram`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://next.api.aliyun.com) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Python

For more information about how to install the SDK for Python, see [Quick start]().

You can download the installation packages of the SDK for Python from the following links:

-   [Alibaba Cloud SDK for Python](https://pypi.python.org/pypi/aliyun-python-sdk-core)
-   [RAM SDK for Python](https://pypi.python.org/pypi/aliyun-python-sdk-ram)

## Example

The following sample code shows how to call the [CreateUser](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/CreateUser.md) API operation by using the SDK for Python. You can use [OpenAPI Explorer](https://next.api.aliyun.com) to debug other API operations and obtain sample code.

```
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkram.request.v20150501.CreateUserRequest import CreateUserRequest
# Construct an Alibaba Cloud client to initiate requests.
# When you construct the client, specify your AccessKey ID and AccessKey secret.
client = AcsClient('<accessKeyId>', '<accessKeySecret>')
# Construct a request.
request = CreateUserRequest()
request.set_accept_format('json')
# Specify request parameters. For more information about the parameters, see API Reference.
request.set_UserName("<UserName>")
# Initiate the request and obtain a response.
response = client.do_action_with_exception(request)
# python2:  print(response)
print(str(response, encoding='utf-8'))
            
```

