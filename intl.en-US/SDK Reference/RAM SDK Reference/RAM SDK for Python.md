# RAM SDK for Python

This topic describes how to install RAM SDK for Python and provides an example about how to use the SDK for Python.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [List of operations by function](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Python

For information about how to install the SDK for Python, see [Quick start]().

You can download the installation packages of the SDK for Python from the following links:

-   [Python SDK](https://pypi.python.org/pypi/aliyun-python-sdk-core)
-   [RAM SDK](https://pypi.python.org/pypi/aliyun-python-sdk-ram)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for Python. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
#! /usr/bin/env python
#coding=utf-8

from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkram.request.v20150501.CreateUserRequest import CreateUserRequest
# Construct an Alibaba Cloud client that is used to initiate requests.
# When you construct the client, specify the AccessKey ID and AccessKey secret.
client = AcsClient('<accessKeyId>', '<accessSecret>', 'cn-hangzhou')
# Construct a request.
request = CreateUserRequest()
request.set_accept_format('json')
# Configure parameters.
request.set_UserName("<UserName>")
# Initiate the request and obtain a response.
response = client.do_action_with_exception(request)
# python2:  print(response)
print(str(response, encoding='utf-8'))
            
```

