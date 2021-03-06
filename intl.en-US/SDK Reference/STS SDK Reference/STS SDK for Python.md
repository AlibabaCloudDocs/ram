# STS SDK for Python

This topic describes how to install STS SDK for Python and provides an example about how to use STS SDK for Python.

## Background information

-   To use STS SDK for Python, you must install the core library of Alibaba Cloud SDK for Python \(`aliyun-python-sdk-core`\) and the STS SDK \(`aliyun-python-sdk-sts`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://next.api.aliyun.com/api/Sts) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md)
-   For information about endpoints to access STS, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Install the SDK for Python

For more information about how to install the SDK for Python, see [Quick start]().

You can download the installation packages of the SDK for Python from the following links:

-   [Python SDK](https://pypi.org/project/aliyun-python-sdk-core)
-   [STS SDK](https://pypi.org/project/aliyun-python-sdk-sts)

## Example

The following sample code shows how to call the AssumeRole API operation by using the SDK for Python. You can use [OpenAPI Explorer](https://next.api.aliyun.com/api/Sts) to debug other API operations and obtain sample code.

```
#!/usr/bin/env python
#coding=utf-8

from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdksts.request.v20150401.AssumeRoleRequest import AssumeRoleRequest

# Construct an Alibaba Cloud client to initiate requests.
# When you construct the client, specify your AccessKey ID and AccessKey secret.
client = AcsClient('<accessKeyId>', '<accessSecret>', 'cn-hangzhou')

# Construct a request.
request = AssumeRoleRequest()
request.set_accept_format('json')

# Specify request parameters.
request.set_RoleArn("<RoleArn>")
request.set_RoleSessionName("<RoleSessionName>")

# Initiate the request and obtain a response.
response = client.do_action_with_exception(request)
# python2:  print(response)
print(str(response, encoding='utf-8'))           
```

