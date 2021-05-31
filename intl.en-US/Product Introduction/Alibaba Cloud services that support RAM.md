# Alibaba Cloud services that support RAM

This topic lists the Alibaba Cloud services that support Resource Access Management \(RAM\), the authorization granularity and system policies for each service, and the links of related topics.

## Overview

You can query Alibaba Cloud services that support RAM based on the following categories:

-   [Elastic computing](#section_01)
-   [Database](#section_02)
-   [Storage](#section_03)
-   [Cloud communications](#section_huy_vgm_381)
-   [Networking](#section_04)
-   [O&M management](#section_0pl_xt2_475)
-   [Middleware](#section_d3u_2ya_hzl)
-   [Media services and CDN](#section_8rc_09n_bas)
-   [Enterprise applications](#section_vzs_r6u_os6)
-   [Domains and websites](#section_do2_b0k_3um)
-   [Artificial intelligence](#section_fho_ls1_75c)
-   [IoT](#section_1cu_n9s_aah)
-   [Big data](#section_13)
-   [Developer services](#section_vl9_4wy_kja)
-   [Security](#section_14)
-   [Technical support](#section_l28_67n_cri)
-   [Marketplace](#section_15)
-   [Others](#section_9k9_8u5_zca)

Each table in this topic contains the following columns:

-   Alibaba Cloud service: the name of the cloud service that supports RAM.
-   Sub-service/Sub-module: the sub-service or sub-module of the cloud service. "-" indicates none.
-   API: indicates whether STS can be used to implement access control when you call the API of the service. A check sign \(✓\) indicates that STS is supported when you call the API of the service. A cross sign \(×\) indicates that STS is not supported when you call the API of the service. A circle \(○\) indicates that no API is provided for that service.
-   API: indicates whether STS can be used to implement access control when you call the API of the service. A check sign \(✓\) indicates that STS is supported when you call the API of the service. A cross sign \(×\) indicates that STS is not supported when you call the API of the service. A circle \(○\) indicates that no API is provided for that service.
-   Authorization granularity: the minimum authorization granularity of the service. A hyphen \(-\) indicates that no authorization granularity is defined.

    The following authorization granularity is defined:

    -   Service: You can control whether RAM users can access the service. You can grant RAM users or RAM roles the permissions to access all or none of the resources in the service.
    -   Operation: You can control whether RAM users can perform specific operations on a type of resource in the service.
    -   Resource: You can control whether RAM users can perform a specific operation on a specific resource in the service. For example, you can authorize a RAM user to restart a specific Elastic Compute Service \(ECS\) instance.
-   System policy: the system policies that RAM provides for the service. A hyphen \(-\) indicates that no system policies are provided for the service.
-   Documentation: the topics that are related to both RAM and the service. A hyphen \(-\) indicates that no topics are related to RAM or the service.

## Elastic computing

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|ECS|ECS|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|Elastic Block Storage \(EBS\)|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|Elastic GPU Service|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|ECS Bare Metal Instance|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|Super Computing Cluster|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|Dedicated Host \(DDH\)|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|ECS|Alibaba Cloud Linux 2|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|Auto Scaling \(ESS\)|-|✓|✓|Service|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[API usage instructions](/intl.en-US/API Reference/API usage instructions.md)|
|Container Service for Kubernetes \(ACK\)|-|✓|✓|Resource|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[Use sub-accounts](/intl.en-US/User Guide/Authorizations/Use sub-accounts.md)|
|Batch Compute|-|✓|✓|Service|-

|-|
|Resource Orchestration Service \(ROS\)|-|✓|✓|Service|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[Use RAM to control resource access](/intl.en-US/Quick Start/Use RAM to control resource access.md)|
|Function Compute|-|✓|✓|Resource|-   AliyunFCFullAccess
-   AliyunFCReadOnlyAccess
-   AliyunFCInvocationAccess

|[Quick start for using the console as RAM users](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|Simple Application Server|-|✓|○|Service|AliyunSWASFullAccess|-|
|Elastic High Performance Computing \(E-HPC\)|-|✓|✓|Service|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|Container Registry|-|✓|✓|Resource|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[Repository access control](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|Elastic Cloud Desktop|Elastic Desktop Service \(EDS\)|✓|✓|Resource|-   AliyunECDFullAccess
-   AliyunECDReadOnlyAccess
-   AliyunECDRamUserAccess

|-|
|Elastic Container Instance \(ECI\)|-|✓|✓|Resource|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[Grant permissions to a RAM user](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|
|Serverless Workflow|-|✓|✓|Resource|-   AliyunFnFFullAccess
-   AliyunFnFReadOnlyAccess

|[Authorization policy](/intl.en-US/API Reference/Authorization policy.md)|
|Web App Service|-|✓|✓|Operation|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|- |

## Database

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|ApsaraDB RDS|ApsaraDB RDS|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB RDS|ApsaraDB RDS for MySQL|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB RDS|ApsaraDB RDS for SQL Server|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB RDS|ApsaraDB RDS for PostgreSQL|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB RDS|ApsaraDB RDS for PPAS|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB RDS|ApsaraDB for MyBase|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|-|
|ApsaraDB for Redis|-|✓|✓|Resource|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|ApsaraDB for Memcache|-|✓|✓|Service|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|ApsaraDB for MongoDB|-|✓|✓|Resource|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|- |
|AnalyticDB for PostgreSQL|-|✓|✓|Resource|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[Authentication rules for APIs](/intl.en-US/API Reference/Use RAM for resource authorization/Authentication rules for APIs.md)|
|Data Transmission Service \(DTS\)|-|✓|✓|Operation|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

|[Authorize a RAM user to use DTS](/intl.en-US/RAM-based Access Control/Use a system policy to authorize a RAM user to manage DTS instances.md)|
|Data Management \(DMS\)|-|✓|✓|Service|-|- |
|AnalyticDB for MySQL|-|✓|✓|Operation|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[RAM users and permissions](RAM users and permissionst1854382.dita#multiTask1017)|
|PolarDB-X|-|✓|✓|Resource|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[Use RAM for resource authorization](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
|ApsaraDB for HBase|-|✓|✓|Resource|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[Use RAM for resource authorization]()|
|Advanced Database & Application Migration \(ADAM\)|-|✓|○|Service|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[Authorize a RAM user to log on to the ADAM console]()|
|PolarDB|-|✓|✓|Operation|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[Create and authorize a RAM user](/intl.en-US/User Guide/Account Management/Create and authorize a RAM user.md)|
|Database Backup|-|✓|✓|Service|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|Database Autonomy Service \(DAS\)|-|✓|✓|Service|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[What can I do if I fail to access DAS as a RAM user due to lack of permissions?](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|Data Lake Analytics \(DLA\)|-|✓|✓|Operation|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess
-   AliyunDLADeveloperAccess

|[Grant RAM users fine-grained permissions to access DLA]()|
|ApsaraDB for OceanBase|-|✓|○|Service|-   AliyunOceanBaseFullAccess
-   AliyunOceanBaseReadOnlyAccess

|-|
|ApsaraDB for Cassandra|-|✓|✓|Resource|-   AliyunCassandraFullAccess
-   AliyunCassandraReadOnlyAccess

|[Manage RAM users]()|
|LedgerDB|-|✓|✓|Resource|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[RAM user authorization]()|
|ApsaraDB for ClickHouse|-|✓|✓|Resource|-   AliyunClickHouseFullAccess
-   AliyunClickHouseReadOnlyAccess

|[RAM-based authorization]()|
|Database Gateway|-|✓|✓|Resource|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|

## Storage

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Object Storage Service \(OSS\)|-|✓|✓|Resource|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[Overview](/intl.en-US/Developer Guide/Data security/Access and control/RAM Policy/Overview.md)|
|Apsara File Storage NAS \(NAS\)|-|✓|✓|Operation|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[Perform access control based on RAM policies]()|
|Tablestore|-|✓|✓|Resource|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[Custom permissions](/intl.en-US/Function Introduction/Authorization management/Custom permissions.md)|
|Cloud Storage Gateway \(CSG\)|-|✓|✓|Service|AliyunHCSSGWFullAccess|[Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md)|
|Hybrid Backup Recovery \(HBR\)|-|✓|○|Resource|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|[Manage user permissions](/intl.en-US/Best Practices/Manage user permissions.md)|
|Hybrid Cloud Storage Array \(CSA\)|-|×|○|-|-|-|

## Cloud communications

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Short Message Service \(SMS\)|-|✓|✓|Service|-

|- |

## Networking

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Virtual Private Cloud \(VPC\)|-|✓|✓|Resource|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Server Load Balancer \(SLB\)|Server Load Balancer \(SLB\)|✓|✓|Resource|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[Authorize a RAM user](/intl.en-US/Classic Load Balancer/CLB Developer Guide/Developer Guide/Authorize a RAM user.md)|
|Server Load Balancer \(SLB\)|Application Load Balancer \(ALB\)|✓|✓|Resource|-   AliyunALBFullAccess
-   AliyunALBReadOnlyAccess

|-|
|Express Connect|-|✓|✓|Resource|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Elastic IP Address \(EIP\)|-|✓|✓|Resource|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|NAT Gateway \(NAT\)|-|✓|✓|Resource|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|VPN Gateway|-|✓|✓|Resource|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|EIP Bandwidth Plan|-|✓|✓|Resource|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|Global Accelerator \(GA\)|-|✓|✓|Resource|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Smart Access Gateway \(SAG\)|-|✓|✓|Resource|-

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|Cloud Enterprise Network \(CEN\)|-|✓|✓|Resource|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[RAM authentication]()|
|PrivateLink|-|✓|✓|Resource|-   AliyunPrivateLinkFullAccess
-   AliyunPrivateLinkReadOnlyAccess

|-   [Manage permissions on PrivateLink by using RAM]()
-   [RAM user authorization]() |
|Alibaba Cloud DNS PrivateZone|-|✓|✓|Resource|-   AliyunPvtzFullAccess
-   AliyunPvtzReadOnlyAccess

|[RAM](https://www.alibabacloud.com/help/doc-detail/65886.htm)|

## O&M management

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Application Real-Time Monitoring Service \(ARMS\)|-|✓|✓|Service|-   AliyunARMSFullAccess
-   AliyunARMSReadOnlyAccess

|[Grant different permissions to RAM users](/intl.en-US/Access Control/Grant different permissions to RAM users.md)|
|CloudMonitor|-|✓|✓|Operation|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess
-   AliyunCloudMonitorMetricDataReadOnlyAccess

|[Control permissions of RAM users](/intl.en-US/Appendix 3 account authorization/Control permissions of RAM users.md)|
|Cloud Shell|-|✓|○|Service|-|-|
|Cloud Config|-|✓|✓|Service|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[Permission verification](/intl.en-US/API Reference/Permission verification.md)|
|Logic Composer|-|✓|✓|Resource|-   AliyunLogicComposerFullAccess
-   AliyunLogicComposerReadOnlyAccess

|[Grant permissions to a RAM user]()|
|Operation Orchestration Service \(OOS\)|-|✓|✓|Resource|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[Access control]()|

## Middleware

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Enterprise Distributed Application Service \(EDAS\)|-|✓|✓|Service|-   AliyunEDASFullAccess
-   AliyunEDASReadOnlyAccess
-   AliyunEDASApplicationFullAccess
-   AliyunEDASApplicationReadOnlyAccess
-   AliyunEDASResourceReadOnlyAccess
-   AliyunEDASResourceFullAccess

|[Manage RAM users]()|
|Message Queue|Message Queue for Apache RocketMQ|✓|✓|Resource|-   AliyunMQFullAccess
-   AliyunMQReadOnlyAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[Grant permissions to RAM users]()|
|Message Queue|Message Queue for MQTT|✓|✓|Resource|-   AliyunMQFullAccess
-   AliyunMQReadOnlyAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[Grant permissions to RAM users]()|
|Message Queue|Message Queue for RabbitMQ|✓|✓|Resource|-   AliyunAMQFullAccess
-   AliyunAMQPReadOnlyAccess

|[Grant permissions to RAM users]()|
|Message Service \(MNS\)|-|✓|✓|Resource|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|[Create a custom policy](Create a custom policyt1835681.dita#task810)|
|Application Configuration Management|-|✓|✓|Resource|AliyunACMFullAccess|[Access control](/intl.en-US/Access Control/Access control.md)|
|Message Queue for Apache Kafka|-|✓|✓|Service|-   AliyunKafkaFullAccess
-   AliyunKafkaReadOnlyAccess

|[Grant permissions to RAM users](/intl.en-US/Access control/Grant permissions to RAM users.md)|
|Application High Availability Service|-|✓|✓|Service|-   AliyunAHASFullAccess
-   AliyunAHASReadOnlyAccess

|- |
|Alibaba Cloud Service Mesh \(ASM\)|-|✓|✓|Resource|-|[Overview](https://www.alibabacloud.com/help/doc-detail/169466.htm)|
|EventBridge|-|✓|✓|Resource|-   AliyunEventBridgeFullAccess
-   AliyunEventBridgeReadOnlyAccess
-   AliyunEventBridgeResourceCreatePolicy
-   AliyunEventBridgeResourceDeletePolicy
-   AliyunEventBridgeResourceUpdatePolicy
-   AliyunEventBridgePutEventsPolicy

|[Policies]()|

## Media services and CDN

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|CDN|-|✓|✓|Resource|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[RAM authentication](/intl.en-US/New API Reference/RAM authentication.md)|
|ApsaraVideo for Media Processing \(MTS\)|-|✓|✓|Service|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|- |
|ApsaraVideo VOD \(VOD\)|-|✓|✓|Operation|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|ApsaraVideo for Live|-|✓|✓|Resource|-   AliyunLiveFullAccess
-   AliyunLiveReadOnlyAccess

|[Sub-account console operating instructions](/intl.en-US/API Reference/Authentication rules on API requests.md)|
|Real-Time Communication|-|✓|✓|Resource|-

|- |
|Dynamic Route for CDN \(DCDN\)|-|✓|✓|Resource|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|

## Enterprise applications

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Direct Mail|-|✓|✓|Service|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API Gateway|-|✓|✓|Service|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[Use RAM to manage user permissions for API Gateway]()|
|Resource Management|Resource Management|✓|✓|Operation|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[RAM authorization]()|
|Resource Management|Tag|✓|✓|Operation|-   AliyunTAGFullAccess
-   AliyunTAGReadOnlyAccess

|[Tag](section_zqv_es3_ege)|
|Blockchain as a Service \(BaaS\)|Blockchain as a Service \(BaaS\)|✓|✓|Resource|-   AliyunBaaSFullAccess
-   AliyunBaaSReadOnlyAccess

|[Hyperledger Fabric RAM authentication](/intl.en-US/API reference/Hyperledger Fabric RAM authentication.md)|
|CloudQuotation \(CQ\)|-|✓|○|Service|-   AliyunCQLoudFullAccess
-   AliyunCQLoudReadOnlyAccess

|-|

## Domains and websites

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Alibaba Cloud DNS \(DNS\)|Alibaba Cloud DNS \(DNS\)|✓|✓|Resource|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|- |
|Alibaba Cloud DNS \(DNS\)|Alibaba Cloud Public DNS|✓|✓|Resource|-   AliyunPubDNSReadOnlyAccess
-   AliyunPubDNSFullAccess

|-|
|Domains|-|✓|✓|Resource|AliyunDomainFullAccess|[Authentication rules for the Domains API](/intl.en-US/Domain name management/Use RAM in Domain Name/Authentication rules for the Domains API.md)|

## Artificial intelligence

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Intelligent Speech Interaction|-|✓|✓|Service|-   AliyunNLSFullAccess
-   AliyunNLSReadOnlyAccess

|-|
|Machine Learning Platform for AI \(PAI\)|-|✓|✓|Service|-|-|
|Image Search|-|✓|✓|Resource|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[Grant permissions to RAM users](https://www.alibabacloud.com/help/zh/doc-detail/179180.htm)|
|Machine Translation|-|✓|✓|Service|-|-|

## IoT

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|IoT Platform|-|✓|✓|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[RAM user access](/intl.en-US/User Accounts/RAM authorization/Resource Access Management (RAM)/RAM user access.md)|
|Link IoT Edge|-|✓|✓|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[Access resources of other Alibaba Cloud services](/intl.en-US/Link IoT Edge/User Guide/Access resources of other Alibaba Cloud services.md)|
|ApsaraDB for Lindorm|Time Series Database \(TSDB\)|✓|✓|Operation|-

|-|

## Big data

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|DataWorks|-|✓|✓|Service|AliyunDataWorksFullAccess|[Use a RAM user]()|
|Quick BI|-|✓|✓|Service|-|-|
|DataV|-|✓|○|Service|AliyunDataVFullAccess|-|
|Realtime Compute for Apache Flink|-|✓|✓|Service|-|-|
|Elasticsearch|-|✓|✓|Resource|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[Types of resources that can be authorized](/intl.en-US/RAM/Types of resources that can be authorized.md)|
|E-MapReduce|-|✓|✓|Service|-   AliyunEMRFullAccess
-   AliyunUEMReadOnlyAccess
-   AliyunEMRFlowAdmin
-   AliyunEMRDevelopAccess

|-|
|Log Service|-|✓|✓|Resource|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[RAM authentication rules](/intl.en-US/Developer Guide/API Reference/RAM/STS/RAM authentication rules.md)|
|Hologres|-|✓|✓|Resource|-   AliyunHologresFullAccess
-   AliyunHologresReadOnlyAccess

|[Use Hologres as a RAM user](/intl.en-US/Preparations/Use Hologres as a RAM user.md)|

## Developer services

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Apsara DevOps|-|✓|✓|Resource|-   AliyunRDCFullAccess
-   AliyunRDCReadOnlyAccess

|-|
|Tracing Analysis|-|✓|✓|Service|-   AliyunTracingAnalysisFullAccess
-   AliyunTracingAnalysisReadOnlyAccess

|-|

## Security

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Security Center \(SAS\)|-|✓|✓|Service|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|Server Guard|-|✓|✓|Service|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|Anti-DDoS|Anti-DDoS|✓|✓|Service|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|Anti-DDoS|Anti-DDoS Pro|✓|✓|Service|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|Anti-DDoS|Anti-DDoS Premium|✓|○|Service|-   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

|-|
|GameShield|-|✓|○|Service|AliyunYundunGameShieldReadOnlyAccess

|-|
|Web Application Firewall \(WAF\)|Web Application Firewall \(WAF\)|✓|✓|Service|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL Certificates Service|-|✓|✓|Service|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|Cloud Firewall \(CFW\)|-|✓|✓|Service|-   AliyunYundunCloudFirewallReadOnlyAccess
-   AliyunYundunCloudFirewallFullAccess

|-|
|Managed Security Service \(MSSP\)|-|✓|○|Service|-|-|
|Content Moderation|-|✓|✓|Service|AliyunYundunGreenWebFullAccess|-|
|Bastionhost|Bastionhost|✓|○|Service|-   AliyunYundunBastionHostFullAccess
-   AliyunYundunBastionHostReadOnlyAccess
-   AliyunYundunBastionHostOperateOnlyAccess
-   AliyunYundunBastionHostAuditOnlyAccess

|-|
|Data Security Center \(DSC\)|-|✓|✓|Service|-   AliyunYundunSDDPFullAccess
-   AliyunYundunSDDPReadOnlyAccess

|-|
|Identity as a Service \(IDaaS\)|-|✓|○|Operation|-   AliyunYundunIdaasFullAccess
-   AliyunYundunIdaasReadOnlyAccess

|-|
|Key Management Service \(KMS\)|-|✓|✓|Resource|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[Use RAM to control access to resources](/intl.en-US/Access Control and Audit/Use RAM to control access to resources.md)|
|Resource Access Management \(RAM\)|-|✓|✓|Resource|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference/API Reference (RAM)/RAM authentication.md)|
|ActionTrail|-|✓|✓|Operation|-

|[RAM account authentication](/intl.en-US/API Reference/API Reference (2017-12-04)/RAM account authentication.md)|

## Technical support

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Ticket Management|-|✓|✓|Service|AliyunSupportFullAccess|-|

## Marketplace

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Alibaba Cloud Marketplace|-|✓|×|Service|AliyunMarketplaceFullAccess|-|

## Others

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|Authorization granularity|System policy|Documentation|
|:--------------------|----------------------|:------|:--|:------------------------|:------------|:------------|
|Billing Management|-|✓|✓|Service|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|- |
|ICP Filing|-|✓|○|Service|AliyunBeianFullAccess|-|

