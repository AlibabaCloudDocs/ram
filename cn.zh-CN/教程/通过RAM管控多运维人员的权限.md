# 通过RAM管控多运维人员的权限

当您的企业涉及多种运维需求时，通过RAM对不同的运维人员授予不同的权限，方便管理和控制。

某企业购买了大量的阿里云服务，并将应用系统部署在云上，因此涉及多种运维需求：

-   不同的运维人员需要管理不同的阿里云服务。
-   不同的运维人员需要拥有不同的访问、操作、管理云资源的权限。

## 解决方案

创建RAM用户，为RAM用户授予不同的权限策略，满足不同场景的运维需求。

|运维人员|权限策略名称|权限策略说明|
|:---|:-----|:-----|
|云运维人员|AdministratorAccess|管理所有阿里云资源的权限|
|虚拟机运维人员|AliyunECSFullAccess|管理云服务器服务（ECS）的权限|
|AliyunESSFullAccess|管理弹性伸缩服务（ESS）的权限|
|AliyunSLBFullAccess|管理负载均衡服务（SLB）的权限|
|AliyunNASFullAccess|管理文件存储服务（NAS）的权限|
|AliyunOSSFullAccess|管理对象存储服务（OSS）权限|
|AliyunOTSFullAccess|管理表格存储服务（OTS）的权限|
|网络运维人员|AliyunCDNFullAccess|管理CDN的权限|
|AliyunCENFullAccess|管理云企业网（CEN）的权限|
|AliyunCommonBandwidthPackageFullAccess|管理共享带宽的权限|
|AliyunEIPFullAccess|管理弹性公网IP（EIP）的权限|
|AliyunExpressConnectFullAccess|管理高速通道（ExpressConnect）的权限|
|AliyunNATGatewayFullAccess|管理NAT网关（NATGateway）的权限|
|AliyunSCDNFullAccess|管理安全加速（SCDN）的权限|
|AliyunSmartAccessGatewayFullAccess|管理智能接入网关（SmartAccessGateway）的权限|
|AliyunVPCFullAccess|管理专有网络（VPC）的权限|
|AliyunVPNGatewayFullAccess|管理VPN网关（VPNGateway）的权限|
|数据库运维人员|AliyunRDSFullAccess|管理云数据库服务（RDS）的权限|
|AliyunDTSFullAccess|管理数据传输服务（DTS）的权限|
|安全运维人员|AliyunYundunFullAccess|管理云盾所有产品（Yundun）的权限|
|监控运维人员|AliyunActionTrailFullAccess|管理操作审计（ActionTrail）的权限|
|AliyunARMSFullAccess|管理业务实时监控服务（ARMS）的权限|
|AliyunCloudMonitorFullAccess|管理云监控（CloudMonitor）的权限|
|ReadOnlyAccess|只读访问所有阿里云资源的权限|
|AliyunSupportFullAccess|管理工单系统的权限|

## 操作步骤

本示例将RAM用户`alice@secloud.onaliyun.com`配置为数据库运维人员，允许该RAM用户管理云数据库服务（RDS）和数据传输服务（DTS）。

1.  使用阿里云账号登录[RAM控制台](https://ram.console.aliyun.com/)。

2.  创建RAM用户`alice@secloud.onaliyun.com`。

    具体操作，请参见[创建RAM用户](/cn.zh-CN/用户管理/基本操作/创建RAM用户.md)。

3.  为RAM用户`alice@secloud.onaliyun.com`授予`AliyunRDSFullAccess`和`AliyunDTSFullAccess`的权限策略。

    具体操作，请参见[为RAM用户授权](/cn.zh-CN/用户管理/授权管理/为RAM用户授权.md)。


您可以重复步骤[1](#step_xdt_sfs_jb5)~步骤[3](#step_3ek_5ei_gma)，创建其他RAM用户并授予对应的权限策略，使其管理不同的云服务。

