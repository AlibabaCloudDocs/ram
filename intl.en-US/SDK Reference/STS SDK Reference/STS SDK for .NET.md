# STS SDK for .NET

This topic describes how to install STS SDK for .NET and provides an example on how to use STS SDK for .NET.

## Background information

-   To use STS SDK for .NET, you must install the core library of Alibaba Cloud SDK for .NET \(aliyun-net-sdk-core\) and the STS SDK \(aliyun-net-sdk-sts\).
-   Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For more information about STS API operations, see .
-   For more information about the endpoint of STS, see .

## Install the SDK for .NET

For more information about how to install the SDK for .NET, see .

You can download the installation packages of the SDK for .NET from the following links:

-   .NET SDK
-   STS SDK

## Example

The following sample code shows how to call the API operation by using the SDK for .NET.You can visit OpenAPI Explorer to debug other API operations and obtain sample code.

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
            // Construct an Alibaba Cloud client to initiate requests.
 // When you construct the client, specify your AccessKey ID and AccessKey secret.
 IClientProfile profile = DefaultProfile.GetProfile("cn-hangzhou", "<accessKeyId>", "<accessSecret>");
            DefaultAcsClient client = new DefaultAcsClient(profile);
             // Construct a request and specify request parameters. For more information about the parameters, see API Reference.
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

