# SDK for Go

This topic describes how to install the SDK for Go and provides an example of how to use the SDK for Go.

## Background information

-   Alibaba Cloud provides [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about Resource Access Management \(RAM\) API operations, see [RAM API Reference](/intl.en-US/API Reference/API Reference (RAM)/List of operations by function.md).

## Install the SDK for Go

For more information about how to install the SDK for Go, see [Get started]().

You can download the installation packages of the SDK for Go from the following links:

-   [Alibaba Cloud SDK for Go](https://github.com/aliyun/alibaba-cloud-sdk-go)
-   [Alibaba Cloud RAM SDK for Go](https://github.com/aliyun/alibaba-cloud-sdk-go/tree/master/services/ram)

## Example

The following code provides an example of how to call the [CreateUser](/intl.en-US/API Reference/API Reference (RAM)/User management APIs/CreateUser.md) operation by using the SDK for Go. You can use [OpenAPI Developer Portal](https://next.api.aliyun.com/api/Ram) to debug other API operations and obtain sample code.

```
package main

import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/ram"
)

func main() {
    // Construct an Alibaba Cloud client that is used to initiate requests.
    // When you construct the client, specify your AccessKey ID and AccessKey secret.
    client, err := ram.NewClientWithAccessKey("<accessKeyId>", "<accessKeySecret>")

    request := ram.CreateCreateUserRequest()
    request.Scheme = "https"
    
    // Specify request parameters. For more information about the parameters, see API Reference.
    request.UserName = "<UserName>"
    // Initiate the request and obtain a response.
    response, err := client.CreateUser(request)
    if err ! = nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

