# STS SDK for .NET

This topic describes how to install STS SDK for .NET and provides an example about how to use the SDK for .NET.

## Background information

-   To use an SDK for .NET, you must install the core library of Alibaba Cloud SDK for .NET\(`aliyun-net-sdk-core`\) and the STS SDK \(`aliyun-net-sdk-sts`\).
-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see [What is STS?](/intl.en-US/API Reference (STS)/What is STS?.md).
-   For information about endpoints to access STS, see [Endpoints](/intl.en-US/API Reference (STS)/Endpoints.md).

## Install the SDK for .NET

For information about how to install the SDK for .NET, see [Get started]().

You can download the installation packages of the SDK for .NET from the following links:

-   [.NET SDK](https://github.com/aliyun/aliyun-openapi-net-sdk/tree/master/aliyun-net-sdk-core)
-   [STS SDK](https://github.com/aliyun/aliyun-openapi-net-sdk/tree/master/aliyun-net-sdk-sts)

## Example

The following code provides an example on how to call the AssumeRole API operation by using the SDK for .NET. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
using System;
using System.Collections.Generic;
using Aliyun.Acs.Core;
using Aliyun.Acs.Core.Exceptions;
using Aliyun.Acs.Core.Profile;
using Aliyun.Acs.Sts.Model.V20150401;

namespace StsDemo
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
            var request = new AssumeRoleRequest();
            request.RoleArn = "<RoleArn>";
            request.RoleSessionName = "<RoleSessionName>";

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

