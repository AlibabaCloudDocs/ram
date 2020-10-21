# RAM SDK for .NET

This topic describes how to install RAM SDK for .NET and provides an example about how to use the SDK for .NET.

## Background information

-   To use an SDK for .NET, you must install the core library of Alibaba Cloud SDK for .NET\(`aliyun-net-sdk-core`\) and the RAM SDK \(`aliyun-net-sdk-ram`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [List of operations by function](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for .NET

For information about how to install the SDK for .NET, see [Get started]().

You can download the installation packages of the SDK for .NET from the following links:

-   [.NET SDK](https://github.com/aliyun/aliyun-openapi-net-sdk/tree/master/aliyun-net-sdk-core)
-   [RAM SDK](https://github.com/aliyun/aliyun-openapi-net-sdk/tree/master/aliyun-net-sdk-ram)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for .NET. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
using System;
using System.Collections.Generic;
using Aliyun.Acs.Core;
using Aliyun.Acs.Core.Exceptions;
using Aliyun.Acs.Core.Profile;
using Aliyun.Acs.Ram.Model.V20150501;

namespace RamDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Construct an Alibaba Cloud client that is used to initiate requests.
            // When you construct the client, specify the AccessKey ID and AccessKey secret.
            IClientProfile profile = DefaultProfile.GetProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
            DefaultAcsClient client = new DefaultAcsClient(profile);

            // Construct a request and configure the request parameters.
            var request = new CreateUserRequest();
            request.UserName = "<UserName>";

            // Initiate the request and obtain a response.
            try {
                var response = client.GetAcsResponse(request);
                Console.WriteLine(System.Text.Encoding.Default.GetString(response.HttpResponse.Content));
            }
            catch (ServerException e)
            {
                Console.WriteLine(e);
            }
            catch (ClientException e)
            {
                Console.WriteLine(e);
            }
        }
    }
}
```

