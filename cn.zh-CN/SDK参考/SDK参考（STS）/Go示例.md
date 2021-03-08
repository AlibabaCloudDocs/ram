# Go示例

本文简要介绍了Go SDK的安装方法，并提供了示例代码。

## 背景信息

-   [OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)提供在线调试API和动态生成SDK示例代码的功能，能显著降低API的使用难度，推荐您使用。
-   关于STS API的详情，请参见[什么是STS](/cn.zh-CN/API参考/API 参考（STS）/什么是STS.md)。
-   关于STS的接入地址，请参见[接入地址](/cn.zh-CN/API参考/API 参考（STS）/接入地址.md)。

## Go SDK的安装方法

Go SDK的安装方法，请参见[快速开始]()。

Go SDK安装包下载地址如下：

-   [Go SDK](https://github.com/aliyun/alibaba-cloud-sdk-go)
-   [STS SDK](https://github.com/aliyun/alibaba-cloud-sdk-go/tree/master/services/sts)

## Go SDK示例

下面为您提供[AssumeRole](/cn.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md) API的Go SDK示例代码。关于其他API，请访问[OpenAPI开发者门户](https://next.api.aliyun.com/api/Sts)调试并获取示例代码。

```
package main

import (
    "fmt"
      "github.com/aliyun/alibaba-cloud-sdk-go/services/sts"
)

func main() {
    
    //构建一个阿里云客户端, 用于发起请求。
    //构建阿里云客户端时，需要设置AccessKey ID和AccessKey Secret。
    client, err := sts.NewClientWithAccessKey("cn-hangzhou", "<AccessKeyId>", "<AccessKeySecret>")
    
    //构建请求对象。
    request := sts.CreateAssumeRoleRequest()
    request.Scheme = "https"
    
    //设置参数。关于参数含义和设置方法，请参见API参考。
    request.RoleArn = "<RoleArn>"
    request.RoleSessionName = "<RoleSessionName>"
    
    //发起请求，并得到响应。
    response, err := client.AssumeRole(request)
    if err != nil {
        fmt.Print(err.Error())
    }
    fmt.Printf("response is %#v\n", response)
}
```

