# Use RAM to manage permissions of O&M engineers

This topic describes how to use RAM to grant permissions to O&M engineers and manage these permissions.

An Alibaba Cloud account is created. To create an Alibaba Cloud account, visit the [account registration page](https://account.alibabacloud.com/register/intl_register.htm).

A company has purchased multiple Alibaba Cloud services and deployed its application systems on the cloud. This results in the following O&M requirements:

-   Different O&M owners are responsible for different Alibaba Cloud services.
-   Different O&M engineers require different permissions to access and manage Alibaba Cloud resources.

## Solution

The company can set an O&M owner, assign different O&M engineers to different O&M requirements, and then attach specified policies to these engineers.

![O&M owner](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1580549951/p37801.png)

## Procedure

This section uses an example to describe how to set a RAM user as the database O&M owner. In this example, the RAM user is `alice@secloud.onaliyun.com`. The RAM user can then manage ApsaraDB for RDS and Data Transmission Service \(DTS\).

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  [Create a RAM user](/intl.en-US/RAM User Management/Create a RAM user.md).

3.  In the **User Logon Name/Display Name** column, find the RAM user.

4.  Click **Add Permissions** in the **Actions** column. In the **Add Permissions** pane, the **Principal** field is automatically filled in.

5.  In the **Authorization Policy Name** column, click `AliyunRDSFullAccess` and `AliyunDTSFullAccess`.

6.  Click **OK**.

7.  Click **Finished**.

    **Note:** The following table describes the policies that you can use to grant other O&M permissions to the RAM user.


|O&M owner|Policy|Description|
|:--------|:-----|:----------|
|O&M owner|AdministratorAccess|Permissions to manage all Alibaba Cloud resources.|
|VM O&M engineer|AliyunECSFullAccess|Permissions to manage Elastic Compute Service \(ECS\).|
|AliyunESSFullAccess|Permissions to manage Auto Scaling \(ESS\).|
|AliyunSLBFullAccess|Permissions to manage Server Load Balancer \(SLB\).|
|AliyunNASFullAccess|Permissions to manage Apsara File Storage NAS.|
|AliyunOSSFullAccess|Permissions to manage Object Storage Service \(OSS\).|
|AliyunOTSFullAccess|Permissions to manage Tablestore.|
|Network O&M engineer|AliyunCDNFullAccess|Permissions to manage Alibaba Cloud CDN.|
|AliyunCENFullAccess|Permissions to manage Cloud Enterprise Network \(CEN\).|
|AliyunCommonBandwidthPackageFullAccess|Permissions to manage EIP Bandwidth Plan.|
|AliyunEIPFullAccess|Permissions to manage Elastic IP Address \(EIP\).|
|AliyunExpressConnectFullAccess|Permissions to manage Express Connect.|
|AliyunNATGatewayFullAccess|Permissions to manage NAT Gateway.|
|AliyunSCDNFullAccess|Permissions to manage Secure Content Delivery Network \(SCDN\).|
|AliyunSmartAccessGatewayFullAccess|Permissions to manage Smart Access Gateway.|
|AliyunVPCFullAccess|Permissions to manage Virtual Private Cloud \(VPC\).|
|AliyunVPNGatewayFullAccess|Permissions to manage VPN Gateway.|
|Database O&M engineer|AliyunRDSFullAccess|Permissions to manage ApsaraDB for RDS.|
|AliyunDTSFullAccess|Permissions to manage Data Transmission Service \(DTS\).|
|Security O&M engineer|AliyunYundunFullAccess|Permissions to manage Alibaba Cloud Security.|
|Monitoring O&M engineer|AliyunActionTrailFullAccess|Permissions to manage ActionTrail.|
|AliyunARMSFullAccess|Permissions to manage Application Real-Time Monitoring Service \(ARMS\).|
|AliyunCloudMonitorFullAccess|Permissions to manage Cloud Monitor.|
|ReadOnlyAccess|Permissions to read all Alibaba Cloud resources. This policy is optional.|
|AliyunSupportFullAccess|Permissions to manage Ticket Management.|

