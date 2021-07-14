# Use RAM to manage permissions of O&M engineers

This topic describes how to use Resource Access Management \(RAM\) to grant permissions to O&M engineers and manage the permissions.

An enterprise has purchased multiple Alibaba Cloud services and deployed its application systems on the cloud. This poses the following O&M requirements:

-   Different O&M engineers are responsible for different Alibaba Cloud services.
-   Different O&M engineers require different permissions to access and manage Alibaba Cloud resources.

## Solution

The enterprise can create RAM users and attach different policies to the RAM users to meet different O&M requirements.

|O&M engineer|Policy|Description|
|:-----------|:-----|:----------|
|Cloud O&M engineers|AdministratorAccess|Permissions to manage all Alibaba Cloud resources.|
|VM O&M engineers|AliyunECSFullAccess|Permissions to manage Elastic Compute Service \(ECS\).|
|AliyunESSFullAccess|Permissions to manage Auto Scaling \(ESS\).|
|AliyunSLBFullAccess|Permissions to manage Server Load Balancer \(SLB\).|
|AliyunNASFullAccess|Permissions to manage Apsara File Storage NAS \(NAS\).|
|AliyunOSSFullAccess|Permissions to manage Object Storage Service \(OSS\).|
|AliyunOTSFullAccess|Permissions to manage Tablestore \(OTS\).|
|Network O&M engineers|AliyunCDNFullAccess|Permissions to manage Alibaba Cloud CDN \(CDN\).|
|AliyunCENFullAccess|Permissions to manage Cloud Enterprise Network \(CEN\).|
|AliyunCommonBandwidthPackageFullAccess|Permissions to manage EIP Bandwidth Plan.|
|AliyunEIPFullAccess|Permissions to manage Elastic IP Address \(EIP\).|
|AliyunExpressConnectFullAccess|Permissions to manage Express Connect.|
|AliyunNATGatewayFullAccess|Permissions to manage NAT Gateway \(NAT\).|
|AliyunSCDNFullAccess|Permissions to manage Secure CDN \(SCDN\).|
|AliyunSmartAccessGatewayFullAccess|Permissions to manage Smart Access Gateway.|
|AliyunVPCFullAccess|Permissions to manage Virtual Private Cloud \(VPC\).|
|AliyunVPNGatewayFullAccess|Permissions to manage VPN Gateway.|
|Database O&M engineers|AliyunRDSFullAccess|Permissions to manage ApsaraDB RDS.|
|AliyunDTSFullAccess|Permissions to manage Data Transmission Service \(DTS\).|
|Security O&M engineers|AliyunYundunFullAccess|Permissions to manage all Alibaba Cloud Security services.|
|Monitoring O&M engineers|AliyunActionTrailFullAccess|Permissions to manage ActionTrail.|
|AliyunARMSFullAccess|Permissions to manage Application Real-Time Monitoring Service \(ARMS\).|
|AliyunCloudMonitorFullAccess|Permissions to manage CloudMonitor.|
|ReadOnlyAccess|Permissions only to read all Alibaba Cloud resources.|
|AliyunSupportFullAccess|Permissions to manage Ticket Management.|

## Procedure

This example describes how to set the RAM user `alice@secloud.onaliyun.com` as a database O&M engineer. Then, the RAM user can manage ApsaraDB RDS and DTS.

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  Create a RAM user named `alice@secloud.onaliyun.com`.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

3.  Attach the `AliyunRDSFullAccess` and `AliyunDTSFullAccess` policies to the RAM user `alice@secloud.onaliyun.com`.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


You can repeat [1](#step_xdt_sfs_jb5) to [3](#step_3ek_5ei_gma) to create other RAM users and attach policies to the RAM users so that the RAM users can manage different cloud services.

