# Alibaba Cloud services that support RAM

This topic lists the Alibaba Cloud services that support Resource Access Management \(RAM\) and the authorization granularity and system policies for each service. It also provides the links to related topics.

## Alibaba Cloud services that support RAM

The following Alibaba Cloud services support RAM: [Elastic computing](#section_01), [Database](#section_02), [Storage and CDN](#section_03), [Networking](#section_04), [Analytics](#section_05), [Cloud communications](#section_06), [Management and monitoring](#section_07), [Application](#section_08), [IoT](#section_lqo_m79_230), [Message queuing](#section_nur_e8z_9qt), [Middleware](#section_09), [Media services](#section_12), [Big data](#section_13), [Security](#section_14), [Marketplace](#section_15), [Domains and websites](#section_16), [Membership services](#section_17), [Billing management](#section_18), [Ticket services](#section_19), and [Messaging](#section_20).

For information about the Alibaba Cloud services that support Security Token Service \(STS\), see [Alibaba Cloud services that support STS](/intl.en-US/Product Introduction/Alibaba Cloud services that support STS.md).

Each table in this topic contains the following columns:

-   Service: the name of the service that supports RAM.
-   Console: indicates whether RAM can be used to implement access control in the console of the service. A check sign \(✓\) indicates that RAM is supported. A cross sign \(×\) indicates that RAM is not supported. A circle \(○\) indicates that no consoles are supported for the service.
-   API: indicates whether RAM can be used to implement access control based on the API of the service. A check sign \(✓\) indicates that RAM is supported based on the API of the service. A cross sign \(×\) indicates that RAM is not supported based on the API of the service. A circle \(○\) indicates that no APIs are provided for the service.
-   Authorization granularity: the minimum authorization granularity of the service. A hyphen \(-\) indicates that no authorization granularity is defined.

    The following authorization granularity is defined:

    -   Service: You can control whether RAM users can access the service. You can grant RAM users the permissions to access all or none of the resources in the service.
    -   Operation: You can control whether RAM users can perform specific operations on a type of resource in the service.
    -   Resource: You can control whether RAM users can perform a specific operation on a specific resource in the service. For example, you can authorize a RAM user to restart a specific Elastic Compute Service \(ECS\) instance.
-   System policy: the system policies that RAM provides for the service. A hyphen \(-\) indicates that no system policies are provided for the service.
-   Reference: the topics that are related to both RAM and the service. A hyphen \(-\) indicates that no topics are related to RAM or the service.

## Elastic computing

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|ECS|✓|✓|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|Auto Scaling \(ESS\)|✓|✓|Service|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[API usage instructions](/intl.en-US/API Reference/API usage instructions.md)|
|Container Service for Kubernetes \(ACK\)|✓|✓|Resource|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[Use RAM users](/intl.en-US/User Guide/Authorizations/Use sub-accounts.md)|
|Container Registry|✓|✓|Resource|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[Repository access control](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|Resource Orchestration Service \(ROS\)|✓|✓|Service|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[Use RAM to control resource access](/intl.en-US/Quick Start/Use RAM to control resource access.md)|
|Batch Compute|✓|✓|Service|-

|-|
|Function Compute|✓|✓|Resource|-   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

|[Quick start for using the console as RAM users](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|Elastic High Performance Computing \(E-HPC\)|✓|✓|Service|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|Simple Application Server|✓|○|Service|AliyunSWASFullAccess|-|
|Elastic Container Instance|✓|✓|Resource|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[Grant permissions to a RAM user](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|
|Web App Service|✓|✓|Operation|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|- |
|Operation Orchestration Service \(OOS\)|✓|✓|Resource|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[Access control](https://www.alibabacloud.com/help/doc-detail/122529.htm)|

## Database

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|PolarDB|✓|✓|Operation|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[Create and authorize a RAM user](/intl.en-US/User Guide/Account Management/Create and authorize a RAM user.md)|
|ApsaraDB RDS|✓|✓|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[Use RAM for resource authorization](/intl.en-US/API Reference/Use RAM for resource authorization.md)|
|ApsaraDB for MongoDB|✓|✓|Resource|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|- |
|ApsaraDB for Redis|✓|✓|Resource|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|ApsaraDB for Memcache|✓|✓|Service|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|ApsaraDB for HBase|✓|✓|Resource|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[Use RAM for resource authorization]()|
|Time Series Database \(TSDB\)|✓|✓|Operation|-

|-|
|AnalyticDB for PostgreSQL|✓|✓|Resource|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[Authentication rules for APIs](/intl.en-US/API Reference/Use RAM for resource authorization/Authentication rules for APIs.md)|
|AnalyticDB for MySQL|✓|✓|Resource|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[t1854382.dita\#multiTask1017]()|
|Data Transmission Service \(DTS\)|✓|✓|Operation|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

|[Use a system policy to authorize a RAM user to manage DTS instances](/intl.en-US/RAM-based Access Control/Use a system policy to authorize a RAM user to manage DTS instances.md)|
|Database Backup|✓|✓|Service|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|Database Autonomy Service \(DAS\)|✓|✓|Service|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[What can I do if I fail to access DAS as a RAM user due to lack of permissions?](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|PolarDB-X|✓|✓|Resource|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[Use RAM for resource authorization](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
|Advanced Database & Application Migration \(ADAM\)|✓|○|Service|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[Authorize a RAM user to log on to the ADAM console]()|
|Database Gateway|✓|✓|Resource|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|
|LedgerDB|✓|✓|Resource|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[RAM user authorization]()|

## Storage and CDN

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Object Storage Service \(OSS\)|✓|✓|Resource|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[Overview](/intl.en-US/Developer Guide/Data security/Access and control/RAM Policy/Overview.md)|
|Apsara File Storage NAS \(NAS\)|✓|✓|Operation|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[Manage a permission group]()|
|Tablestore|✓|✓|Resource|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[Custom permissions](/intl.en-US/Function Introduction/Authorization management/Custom permissions.md)|
|Cloud Storage Gateway \(CSG\)|✓|✓|Service|AliyunHCSSGWFullAccess|-|
|Hybrid Backup Recovery \(HBR\)|✓|○|Resource|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|-|
|Lightning Cube|✓|○|Service|AliyunMGWFullAccess|-|
|Dynamic Route for CDN \(DCDN\)|✓|✓|Resource|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|CDN|✓|✓|Resource|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[RAM authentication](/intl.en-US/New API Reference/RAM authentication.md)|

## Networking

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Virtual Private Cloud \(VPC\)|✓|✓|Resource|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Server Load Balancer \(SLB\)|✓|✓|Resource|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[Authorize a RAM user](/intl.en-US/Classic Load Balancer/CLB Developer Guide/Developer Guide/Authorize a RAM user.md)|
|Elastic IP Address \(EIP\)|✓|✓|Resource|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Express Connect|✓|✓|Resource|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|NAT Gateway \(NAT\)|✓|✓|Resource|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|VPN Gateway|✓|✓|Resource|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|EIP Bandwidth Plan|✓|✓|Resource|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|Global Accelerator \(GA\)|✓|✓|Resource|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[RAM user authorization](/intl.en-US/API reference/RAM user authorization.md)|
|Smart Access Gateway|✓|✓|Resource|-

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|Cloud Enterprise Network|✓|✓|Resource|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[RAM authentication]()|
|PrivateLink|✓|✓|Resource|-|-   [Manage permissions on PrivateLink by using RAM]()
-   [RAM user authorization]() |

## Analytics

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|E-MapReduce|✓|✓|Service|-   AliyunEMRFullAccess
-   AliyunEMRDevelopAccess
-   AliyunEMRFlowAdmin

|-|
|Data Lake Analytics \(DLA\)|✓|✓|Operation|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

|-|

## Cloud communications

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Short Message Service \(SMS\)|✓|✓|Service|-

|- |

## Management and monitoring

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|CloudMonitor|✓|✓|Operation|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

|[Control permissions of RAM users](/intl.en-US/Appendix 3 account authorization/Control permissions of RAM users.md)|
|ActionTrail|✓|✓|Resource|-

|[RAM account authentication](/intl.en-US/API Reference/API Reference (2017-12-04)/RAM account authentication.md)|
|RAM|✓|✓|Resource|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference/API Reference (RAM)/RAM authentication.md)|
|Key Management Service \(KMS\)|✓|✓|Resource|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[Use RAM to control access to resources](/intl.en-US/Access Control and Audit/Use RAM to control access to resources.md)|
|Intelligent Advisor|×|×|Operation|-|-|
|Resource Management|✓|✓|Resource|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[RAM authorization]()|
|Cloud Config|✓|✓|Service|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[Permission verification](/intl.en-US/API Reference/Permission verification.md)|
|Tag|✓|✓|Operation|-   AliyunTAGFullAccess
-   AliyunTAGReadOnlyAccess

|[Tag](section_zqv_es3_ege)|

## Application

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Log Service|✓|✓|Resource|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[RAM authentication rules](/intl.en-US/Developer Guide/API Reference/RAM/STS/RAM authentication rules.md)|
|Direct Mail|✓|✓|Service|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API Gateway|✓|✓|Service|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[Use RAM to manage user permissions for API Gateway]()|
|Blockchain as a Service \(BaaS\)|✓|✓|Resource|-|[Hyperledger Fabric RAM authentication](/intl.en-US/API reference/Hyperledger Fabric RAM authentication.md)|
|Mini Program Cloud|✓|✓|Operation|-   AliyunMPCAFullAccess
-   AliyunMPCAReadOnlyAccess

|-|

## IoT

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|IoT Platform|✓|✓|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[RAM user access](/intl.en-US/User Accounts/RAM authorization/Resource Access Management (RAM)/RAM user access.md)|
|Link IoT Edge|✓|✓|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[Access resources of other Alibaba Cloud services](/intl.en-US/Link IoT Edge/User Guide/Access resources of other Alibaba Cloud services.md)|

## Message queuing

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Message Queue for Apache RocketMQ|✓|✓|Resource|-   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[Grant permissions to RAM users](https://www.alibabacloud.com/help/zh/doc-detail/61382.htm)|
|Message Service \(MNS\)|✓|✓|Resource|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|- |

## Middleware

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Enterprise Distributed Application Service \(EDAS\)|✓|✓|Service|AliyunEDASFullAccess|[Manage RAM users](https://www.alibabacloud.com/help/zh/doc-detail/44023.htm)|
|Application Real-Time Monitoring Service \(ARMS\)|✓|✓|Service|AliyunARMSFullAccess|[Grant different permissions to RAM users](/intl.en-US/Access Control/Grant different permissions to RAM users.md)|
|Application Configuration Management|✓|✓|Resource|AliyunACMFullAccess|[Access control](/intl.en-US/Access Control/Access control.md)|
|Global Transaction Service \(GTS\)|✓|✓|Service|-   AliyunGTSFullAccess
-   AliyunGTSReadOnlyAccess

|-|

## Media services

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|ApsaraVideo for Media Processing \(MTS\)|✓|✓|Service|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|[Sub-account console operating instructions]()|
|ApsaraVideo VOD \(VOD\)|✓|✓|Service|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|ApsaraVideo Live|✓|✓|Resource|AliyunLiveFullAccess|[Authentication rules on API requests](/intl.en-US/API Reference/Authentication rules on API requests.md)|
|Real-Time Communication|✓|✓|Resource|-

|- |
|Cloud Video Conferencing|✓|○|Resource|-   AliyunCVCFullAccess
-   AliyunCVCReadOnlyAccess

|-|

## Big data

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|DataWorks|✓|✓|Service|AliyunDataWorksFullAccess|[Use a RAM user]()|
|Quick BI|✓|✓|Service|-|-|
|Machine Learning Platform for AI|✓|✓|Service|-|-|
|Public Recognition|✓|✓|Service|-|-|
|DataV|✓|✓|Service|-|-|
|MaxCompute|✓|✓|Service|-|-|
|Elasticsearch|✓|✓|Resource|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[Types of resources that can be authorized](/intl.en-US/RAM/Types of resources that can be authorized.md)|
|Machine Translation|×|×|Service|-|-|
|Image Search|✓|✓|Resource|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[Grant permissions to RAM users](https://www.alibabacloud.com/help/zh/doc-detail/179180.htm)|

## Security

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Security Center \(SAS\)|✓|✓|Service|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|Server Guard|✓|✓|Service|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|Anti-DDoS|✓|✓|Service|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|Anti-DDoS Pro|✓|✓|Service|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|Anti-DDoS Premium|✓|○|Service|-   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

|-|
|GameShield|✓|○|Service|AliyunYundunGameShieldReadOnlyAccess

|-|
|Web Application Firewall \(WAF\)|✓|✓|Service|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL Certificates Service|✓|✓|Service|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|Cloud Security Scanner|✓|✓|Service|AliyunYundunAvdsFullAccess|-|
|Content Moderation|✓|✓|Service|AliyunYundunGreenWebFullAccess|-|
|Anti-Bot Service|✓|○|Service|-   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

|-|
|ID Verification|✓|✓|Service|-   AliyunAntCloudAuthFullAccess
-   AliyunAntCloudAuthReadOnlyAccess

|-|

## Marketplace

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Alibaba Cloud Marketplace|✓|×|Service|AliyunMarketplaceFullAccess|-|

## Domains and websites

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Alibaba Cloud DNS \(DNS\)|✓|✓|Resource|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|-|
|Domains|✓|✓|Resource|AliyunDomainFullAccess|[Authentication rules for the Domains API](/intl.en-US/Domain name management/Use RAM in Domain Name/Authentication rules for the Domains API.md)|
|Cloud Web Hosting|×|×|-|-|-|
|Alibaba Mail|×|×|-|-|-|

## Membership services

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|ICP Filing|✓|○|Service|AliyunBeianFullAccess|-|

## Billing management

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Billing Management|✓|✓|Service|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|- |

## Ticket services

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Ticket Management|✓|✓|Service|AliyunSupportFullAccess|-|

## Messaging

|Service|Console|API|Authorization granularity|System policy|Documentation|
|:------|:------|:--|:------------------------|:------------|:------------|
|Message Center|✓|○|Service|AliyunNotificationsFullAccess|-|

