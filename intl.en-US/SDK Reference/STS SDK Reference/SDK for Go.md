# SDK for Go

This topic describes how to install the SDK for Go and provides an example of how to use the SDK for Go.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about Security Token Service \(STS\) API operations, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md).
-   For information about the endpoints of STS, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Install the SDK for Go

For more information about how to install the SDK for Go, see [Get started]().

You can download the installation packages of the SDK for Go from the following links:

-   [Alibaba Cloud SDK for Go](https://github.com/aliyun/alibaba-cloud-sdk-go)
-   [Alibaba Cloud STS SDK for Go](https://github.com/aliyun/alibaba-cloud-sdk-go/tree/master/services/sts)

## Example

The following code provides an example of how to call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation by using the SDK for Go. You can use [OpenAPI Explorer](https://api.aliyun.com/) to debug other API operations and obtain sample code.

```
package main

import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/sts"
)

func main() {
    
    // Construct an Alibaba Cloud client that is used to initiate requests.
    // When you construct the client, specify your AccessKey ID and AccessKey secret.
    client, err := sts.NewClientWithAccessKey("cn-hangzhou", "<AccessKeyId>", "<AccessKeySecret>")
    
    // Construct a request.
    request := sts.CreateAssumeRoleRequest()
    request.Scheme = "https"
    
    // Specify request parameters. For more information about the parameters, see API Reference.
    request.RoleArn = "<RoleArn>"
    request.RoleSessionName = "<RoleSessionName>"
    
    // Initiate the request and obtain a response.
    response, err := client.AssumeRole(request)
    if err ! = nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

