# 通过RAM对CDN进行权限管理

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对内容分发网络（CDN）进行权限管理，以满足RAM用户操作CDN的多种需求。

-   使用RAM对CDN进行权限管理前，请先了解以下系统策略：

    -   AliyunCDNFullAccess：管理CDN的权限。
    -   AliyunCDNReadOnlyAccess：只读访问CDN的权限。
    当系统策略不能满足您的需求时，您可以创建自定义策略。

-   使用RAM对CDN进行权限管理前，请先了解CDN的权限定义。更多信息，请参见[RAM鉴权](/intl.zh-CN/旧版API参考/RAM鉴权.md)。

1.  创建RAM用户。

    具体操作，请参见[创建RAM用户](/intl.zh-CN/用户管理/基本操作/创建RAM用户.md)。

2.  创建自定义策略。

    具体操作，请参见[创建自定义策略](/intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md)。

    策略示例：授权RAM用户执行CDN只读、刷新缓存及预热的操作。您可以根据需要修改自定义策略内容，从而授权RAM用户不同的权限。关于`Action`或`Resource`的使用规则，请参见[权限策略基本元素](/intl.zh-CN/权限策略管理/权限策略语言/权限策略基本元素.md)。

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "cdn:Describe*",
            "cdn:PushObjectCache",
            "cdn:RefreshObjectCaches"
          ],
          "Resource": "acs:cdn:*:*:*",
          "Effect": "Allow"
        }
      ]
    }
    ```

3.  为RAM用户授权。

    具体操作，请参见[为RAM用户授权](/intl.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


