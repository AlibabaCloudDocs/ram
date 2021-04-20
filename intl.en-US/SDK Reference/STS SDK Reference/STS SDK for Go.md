# STS SDK for Go

This topic describes how to install STS SDK for Go and provides an example of how to use the SDK for Go.

## Background information

-   Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to debug API operations and dynamically generate SDK sample code.
-   For information about STS API operations, see .
-   For information about endpoints to access STS, see .

## Install the SDK for Go

For information about how to install the SDK for Go, see .

You can download the installation packages of the SDK for Go from the following links:

-   Go SDK
-   STS SDK

## Example

The following sample code shows how to call the API operation by using STS SDK for Go.You can use OpenAPI Explorer to debug other API operations and obtain sample code.

```
package main
 import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/sts"
)
 func main() {
     // Construct an Alibaba Cloud client to initiate requests.
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
    if err != nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

