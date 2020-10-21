# RAM SDK for Go

This topic describes how to install RAM SDK for Go and provides an example about how to use the SDK for Go.

## Background information

-   Alibaba Cloud provides [OpenAPI Explorer](https://api.aliyun.com/) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about RAM API operations, see [RAM API](/intl.en-US/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Go

For information about how to install the SDK for Go, see [Get started]().

You can download the installation packages of the SDK for Go from the following links:

-   [Go SDK](https://github.com/aliyun/alibaba-cloud-sdk-go)
-   [RAM SDK](https://github.com/aliyun/alibaba-cloud-sdk-go/tree/master/services/ram)

## Example

The following code provides an example on how to call the CreateUser API operation by using the SDK for Go. For information about other API operations, visit [OpenAPI Explorer](https://api.aliyun.com/), debug API operations, and obtain sample code.

```
package main

import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/ram"
)

func main() {
    // Construct an Alibaba Cloud client that is used to initiate requests.
    // When you construct the client, specify the AccessKey ID and AccessKey secret.
    client, err := ram.NewClientWithAccessKey("cn-hangzhou", "<accessKeyId>", "<accessSecret>")

    request := ram.CreateCreateUserRequest()
    request.Scheme = "https"
    
    // Configure parameters.
    request.UserName = "<UserName>"
    // Initiate a request and obtain a response.
    response, err := client.CreateUser(request)
    if err ! = nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

