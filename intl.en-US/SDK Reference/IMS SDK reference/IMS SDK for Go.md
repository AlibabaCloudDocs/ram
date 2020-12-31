# IMS SDK for Go

This topic describes how to install Identity Management Service \(IMS\) SDK for Go and provides an example on how to use IMS SDK for Go.

## Background information

For more information about IMS API operations, see [List of operations by function](/intl.en-US/API Reference/API Reference (IMS)/List of operations by function.md).

## Install IMS SDK for Go

Run the following command to install IMS SDK for Go:

```
go get github.com/alibabacloud-go/ims-20190815/client
```

To download the installation package of IMS SDK for Go, click [Alibaba Cloud IMS SDK for Go](https://github.com/alibabacloud-go/ims-20190815).

## Sample code

The following code provides an example on how to call the [CreateUser](/intl.en-US/API Reference/API Reference (IMS)/User management/CreateUser.md) API operation by using IMS SDK for Go.

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
* Initialization  Initializes common request parameters.
 */
func Initialization() (_result *ims.Client, _err error) {
  config := &rpc.Config{}
  // The AccessKey ID.
  config.AccessKeyId = tea.String("<AccessKeyId>")
  // The AccessKey secret.
  config.AccessKeySecret = tea.String("<AccessKeySecret>")
  // The ID of the region.
  config.RegionId = tea.String("<RegionId>")
  _result = &ims.Client{}
  _result, _err = ims.NewClient(config)
  return _result, _err
}

/**
* CreateUser  Creates a RAM user.
 */
func CreateUser(client *ims.Client, userPrincipalName *string, displayName *string) (_err error) {
  req := &ims.CreateUserRequest{}
  // The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
  req.UserPrincipalName = userPrincipalName
  // The display name of the RAM user.
  req.DisplayName = displayName
  resp, _err := client.CreateUser(req)
  if _err ! = nil {
    return _err
  }

  fmt.Println("-------------------- Creates a RAM user --------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  return _err
}

/**
* GetDefaultDomain  Obtains the default domain name of your Alibaba Cloud account.
 */
func GetDefaultDomain(client *ims.Client) (_result *string, _err error) {
  req := &ims.GetDefaultDomainRequest{}
  resp, _err := client.GetDefaultDomain(req)
  if _err ! = nil {
    return _result, _err
  }

  fmt.Println("-------------------- Obtains the default domain name of your Alibaba Cloud account --------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  _result = resp.DefaultDomainName
  return _result, _err
}

/**
* GetUser  Queries detailed information about a RAM user.
 */
func GetUser(client *ims.Client, userPrincipalName *string) (_err error) {
  req := &ims.GetUserRequest{}
  // The logon name of the RAM user.
  req.UserPrincipalName = userPrincipalName
  resp, _err := client.GetUser(req)
  if _err ! = nil {
    return _err
  }

  fmt.Println("-------------------- Queries detailed information about a RAM user. --------------------")
  fmt.Println(tea.StringValue(util.ToJSONString(tea.ToMap(resp))))
  return _err
}

func _main(args []*string) (_err error) {
  tryErr := func() (_e error) {
    defer func() {
      if r := tea.Recover(recover()); r ! = nil {
        _e = r
      }
    }()
    client, _err := Initialization()
    if _err ! = nil {
      return _err
    }

    defaultDomain, _err := GetDefaultDomain(client)
    if _err ! = nil {
      return _err
    }

    userName := tea.String("<UserName>")
    // The logon name of the RAM user. Set the logon name in the <username>@<AccountAlias>.onaliyun.com format. <username> indicates the username of the RAM user. <AccountAlias>.onaliyun.com indicates the default domain name.
    userPrincipalName := tea.String(tea.StringValue(userName) + "@" + tea.StringValue(defaultDomain))
    // The display name of the RAM user.
    displayName := tea.String("<DisplayName>")
    _err = CreateUser(client, userPrincipalName, displayName)
    if _err ! = nil {
      return _err
    }
    _err = GetUser(client, userPrincipalName)
    if _err ! = nil {
      return _err
    }

    return nil
  }()

  if tryErr ! = nil {
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
  if err ! = nil {
    panic(err)
  }
}
```

