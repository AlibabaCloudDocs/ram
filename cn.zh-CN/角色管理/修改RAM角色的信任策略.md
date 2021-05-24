# 修改RAM角色的信任策略

通过修改RAM角色的信任策略内容，可以修改RAM角色的可信实体。本文通过示例为您介绍如何修改RAM角色的可信实体为阿里云账号、阿里云服务或身份提供商。

创建RAM角色时，您可以直接选择RAM角色的可信实体为阿里云账号、阿里云服务或身份提供商。一般情况下，创建RAM角色后，您不需要主动修改RAM角色的可信实体。如果某些特殊场景下确有需要，您可以通过本文所述的几种方式修改。修改后请务必进行测试并确保功能可以正常使用。

## 操作步骤

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  在左侧导航栏，单击**RAM角色管理**。

3.  在RAM角色管理页面，单击目标RAM角色名称。

4.  单击**信任策略管理**页签，然后单击**修改信任策略**。

5.  修改信任策略内容，然后单击**确定**。


## 示例一：修改RAM角色的可信实体为阿里云账号

若`Principal`中有`RAM`字段，表示该RAM角色的可信实体为**阿里云账号**，即可以被受信阿里云账号下授权的RAM用户、RAM角色扮演。

以下述信任策略为例：该RAM角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下授权的任何RAM用户、RAM角色扮演。

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:root"
                ]
            }
        }
    ],
    "Version": "1"
}
```

若您将`Principal`中的内容更改如下，则表示该RAM角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下的RAM用户`testuser`扮演。

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"
                ]
            }                   
```

**说明：** 修改此策略时，请确保已创建好RAM用户`testuser`。

若您将`Principal`中的内容更改如下，则表示该RAM角色可以被阿里云账号（AccountID=123456789012\*\*\*\*）下的RAM角色`testrole`扮演。

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:role/testrole"                
                ]
            }                                 
```

**说明：** 修改此策略时，请确保已创建好RAM角色`testrole`。

## 示例二：修改RAM角色的可信实体为阿里云服务

若`Principal`中有`Service`字段，表示该RAM角色的可信实体为**阿里云服务**，即可以被受信云服务扮演。

以下述信任策略为例：该RAM角色可以被当前阿里云账号下的ECS服务扮演。

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Service": [
                    "ecs.aliyuncs.com"
                ]
            }
        }
    ],
    "Version": "1"
}
```

## 示例三：修改RAM角色的可信实体为身份提供商

若`Principal`中有`Federated`字段，表示该RAM角色的可信实体为**身份提供商**，即可以被受信身份提供商下的用户扮演。

以下述信任策略为例：该RAM角色可以被当前阿里云账号（AccountID=123456789012\*\*\*\*）中的身份提供商`testprovider`下的用户扮演。

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Federated": [
                    "acs:ram::123456789012****:saml-provider/testprovider"
                ]
            },
            "Condition":{
                "StringEquals":{
                    "saml:recipient":"https://signin.aliyun.com/saml-role/sso"
                }
            }
        }
    ],
    "Version": "1"
}
```

## 说明

服务关联角色的信任策略由关联的云服务定义，您不能修改服务关联角色的信任策略。更多信息，请参见[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。

