# RAM角色和STS Token常见问题

本文介绍了一些RAM角色和STS Token的常见问题，为您提供说明和指导。

## RAM角色有几种类型？

根据RAM可信实体的不同，RAM支持以下三种类型的角色：

-   **阿里云账号**
-   **阿里云服务**
-   **身份提供商**

## 三种类型的RAM角色分别可以被谁扮演？

-   **阿里云账号**：允许RAM用户所扮演的角色。扮演角色的RAM用户可以属于自己的阿里云账号，也可以属于其他阿里云账号。此类角色主要用来解决跨账号访问和临时授权问题。
-   **阿里云服务**：允许云服务所扮演的角色。特别的是，ECS实例RAM角色也属于这个类型，其可信实体为ECS服务，详情请参见[使用实例RAM角色访问其他云产品](/intl.zh-CN/最佳实践/使用实例RAM角色访问其他云产品.md)。此类角色主要用于授权云服务代理您进行资源操作。
-   **身份提供商**：允许受信身份提供商下的用户所扮演的角色。此类角色主要用于实现与阿里云的SSO。

## 能否指定RAM用户具体可以扮演哪个RAM角色？

您也可以通过创建自定义策略指定RAM用户具体可以扮演的RAM角色。策略示例如下所示：

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Resource": "acs:ram:*:$accountId:role/$roleName"
        }
    ],
    "Version": "1"
}
```

**说明：**

-   上述自定义策略中的`Resource`为角色ARN，关于如何查看角色ARN，请参见[如何查看RAM角色的ARN](#section_qbw_mhy_173)。其中，`$accountId`为阿里云账号ID，`$roleName`为RAM角色名称。
-   将上述自定义策略授权给RAM用户，便可以指定具体可以扮演的RAM角色。关于如何为RAM用户授权，请参见[为RAM用户授权](/intl.zh-CN/用户管理/为RAM用户授权.md)。

## 如何查看RAM角色的ARN？

1.  登录[RAM控制台](https://ram.console.aliyun.com/)。
2.  在左侧导航栏，单击**RAM角色管理**。
3.  单击目标RAM角色名称。
4.  在**基本信息**区域，查看RAM角色ARN。

    ![ RAM角色ARN](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6585537161/p60601.png)


## 为什么使用STS时会报错？

如果一个RAM用户使用API、CLI或SDK调用[AssumeRole](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md)获取STS Token时，出现如下报错信息：

```
Error message: You are not authorized to do this action. You should be authorized by RAM.
```

问题原因和解决方法如下：

-   该RAM用户缺少允许STS扮演角色的权限策略：请为该RAM用户添加系统策略（AliyunSTSAssumeRoleAccess）或自定义策略，详情请参见[能否指定RAM用户具体可以扮演哪个RAM角色](#section_c5c_e3t_at9)。
-   RAM角色的信任策略不包含您正在使用的RAM用户，即RAM角色不允许该RAM用户扮演：请为RAM角色添加允许该RAM用户扮演的信任策略，详情请参见[修改RAM角色的信任策略](/intl.zh-CN/角色管理/修改RAM角色的信任策略.md)。

## STS服务调用次数是否有上限？

AssumeRole接口调用次数限制：每秒最多调用100次，且一个阿里云账号及该账号下的RAM用户、RAM角色共用这100次。当请求量超过100次时，超出部分会报错，报错信息如下：

```
Request was denied due to user flow control
```

## STS Token的权限限制是什么？

STS Token的权限：指定角色的权限与调用[AssumeRole](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md)接口时所设置的`Policy`的交集。

**说明：** 若在调用AssumeRole接口时不设置Policy参数，则返回的STS Token将拥有指定角色的所有权限。

## STS Token的有效期是多久？

STS Token的有效期最小值为900秒，最大值为角色最大会话时间设置的值，默认值为3600秒。

**说明：**

-   您可以通过[AssumeRole](/intl.zh-CN/API参考/API 参考（STS）/操作接口/AssumeRole.md)接口的DurationSeconds参数来限制STS Token的有效期。
-   您可以通过控制台或API设置角色最大会话时间，详情请参见[设置角色最大会话时间](/intl.zh-CN/角色管理/设置角色最大会话时间.md)。

## STS获取的多个Token是否同时有效？

STS Token在过期之前都是有效的，无论是否创建了新的STS Token。

## STS Token发生泄漏时如何处理？

如果您通过扮演角色获取的安全令牌（STS Token）发生泄漏，您可以按以下步骤回收所有已经颁发的STS Token。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。
2.  移除角色的所有权限策略。

    具体操作，请参见[为RAM角色移除权限](/intl.zh-CN/角色管理/为RAM角色移除权限.md)。

3.  删除角色。

    具体操作，请参见[删除RAM角色](/intl.zh-CN/角色管理/删除RAM角色.md)。

    删除角色后，所有通过扮演该角色获取的且未过期的STS Token都将立即失效。


如果您还需要使用该角色，您可以重新创建同名角色并授权相同的权限策略，使用新创建的角色继续完成您的任务。

