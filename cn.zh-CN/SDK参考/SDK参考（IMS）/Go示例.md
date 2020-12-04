# Go示例

本文简要介绍了Go SDK的安装方法，并提供了示例代码。

## 背景信息

关于IMS API的详情，请参见[API概览](/cn.zh-CN/API参考/API 参考（IMS）/API概览.md)。

## Go SDK的安装方法

执行以下命令，安装Go SDK：

```
go get github.com/alibabacloud-go/ims-20190815/client
```

Go SDK安装包下载地址：[Alibaba Cloud IMS SDK for Go](https://github.com/alibabacloud-go/ims-20190815) 。

## Go SDK示例

下面为您提供[CreateUser](/cn.zh-CN/API参考/API 参考（IMS）/用户管理/CreateUser.md) API的Go SDK示例代码。

```
// This file is auto-generated, don't edit it. Thanks.
package main

import (
  "fmt"
  "os"

  ims "github.com/alibabacloud-go/ims-20190815/client"
  rpc "github.com/alibabacloud-go/tea-rpc/client"
  util "github.com/alibabacloud-go/tea-utils/service"
  "github.com/alibabacloud-go/tea/tea"
)

/**
* Initialization  初始化公共请求参数
 */
func Initialization() (_result *ims.Client, _err error) {
  config := &rpc.Config{}
  // 您的AccessKey ID
  config.AccessKeyId = tea.String("<AccessKeyId>")
  // 您的AccessKey Secret
  config.AccessKeySecret = tea.String("<AccessKeySecret>")
  // 您的地域ID
  config.RegionId = tea.String("<RegionId>")
  _result = &ims.Client{}
  _result, _err = ims.NewClient(config)
  return _result, _err
}

/**
* CreateUser  创建RAM用户
 */
func CreateUser(client *ims.Client, userPrincipalName *string, displayName *string) (_err error) {
  req := &ims.CreateUserRequest{}
  // RAM用户的登录名称。格式为<username>@<AccountAlias>.onaliyun.com，其中<username>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
  req.UserPrincipalName = userPrincipalName
  // RAM用户的显示名称
  req.DisplayName = displayName
  resp, _err := client.CreateUser(req)
  if _err != nil {
    return _err
  }

  fmt.Println("--------------------创建RAM用户--------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  return _err
}

/**
* GetDefaultDomain  获取阿里云账号默认域名
 */
func GetDefaultDomain(client *ims.Client) (_result *string, _err error) {
  req := &ims.GetDefaultDomainRequest{}
  resp, _err := client.GetDefaultDomain(req)
  if _err != nil {
    return _result, _err
  }

  fmt.Println("--------------------获取阿里云账号默认域名--------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  _result = resp.DefaultDomainName
  return _result, _err
}

/**
* GetUser  查询RAM用户的详细信息
 */
func GetUser(client *ims.Client, userPrincipalName *string) (_err error) {
  req := &ims.GetUserRequest{}
  // RAM用户的登录名称
  req.UserPrincipalName = userPrincipalName
  resp, _err := client.GetUser(req)
  if _err != nil {
    return _err
  }

  fmt.Println("--------------------查询RAM用户的详细信息--------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  return _err
}

func _main(args []*string) (_err error) {
  tryErr := func() (_e error) {
    defer func() {
      if r := tea.Recover(recover()); r != nil {
        _e = r
      }
    }()
    client, _err := Initialization()
    if _err != nil {
      return _err
    }

    defaultDomain, _err := GetDefaultDomain(client)
    if _err != nil {
      return _err
    }

    userName := tea.String("<UserName>")
    // RAM用户的登录名称。格式为<UserName>@<AccountAlias>.onaliyun.com，其中<UserName>为RAM用户名称，<AccountAlias>.onaliyun.com为默认域名
    userPrincipalName := tea.String(tea.StringValue(userName) + "@" + tea.StringValue(defaultDomain))
    // RAM用户的显示名称
    displayName := tea.String("<DisplayName>")
    _err = CreateUser(client, userPrincipalName, displayName)
    if _err != nil {
      return _err
    }
    _err = GetUser(client, userPrincipalName)
    if _err != nil {
      return _err
    }

    return nil
  }()

  if tryErr != nil {
    var error = &tea.SDKError{}
    if _t, ok := tryErr.(*tea.SDKError); ok {
      error = _t
    } else {
      error.SetErrMsg(tryErr.Error())
    }
    fmt.Println(tea.StringValue(error.Message))
  }
  return _err
}

func main() {
  err := _main(tea.StringSlice(os.Args))
  if err != nil {
    panic(err)
  }
}
```

