# STS SDK for Go

This topic describes how to install STS SDK for Go and provides an example about how to use the SDK for Go.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see [What is STS?](/intl.en-US/API Reference (STS)/What is STS?.md).
-   For information about endpoints to access STS, see [Endpoints](/intl.en-US/API Reference (STS)/Endpoints.md).

## Install the SDK for Go

For information about how to install the SDK for Go, see [Get started]().

You can download the installation packages of the SDK for Go from the following links:

-   [Go SDK](https://github.com/aliyun/alibaba-cloud-sdk-go)
-   [STS SDK](https://github.com/aliyun/alibaba-cloud-sdk-go/tree/master/services/sts)

## Example

The following code provides an example on how to call the AssumeRole API operation by using the SDK for Go. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
package main

import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/sts"
)

func main() {
    
    // Construct an Alibaba Cloud client that is used to initiate requests.
    // When you construct the client, specify the AccessKey ID and AccessKey secret.
    client, err := sts.NewClientWithAccessKey("cn-hangzhou", "<accessKeyId>", "<accessSecret>")
    
    // Construct the request object.
    request := sts.CreateAssumeRoleRequest()
    request.Scheme = "https"
    
    // Configure parameters.
    request.RoleArn = "<RoleArn>"
    request.RoleSessionName = "<RoleSessionName>"
    
    // Initiate a request and obtain a response.
    response, err := client.AssumeRole(request)
    if err ! = nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

