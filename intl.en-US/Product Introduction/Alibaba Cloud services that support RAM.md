# Alibaba Cloud services that support RAM

This topic lists the Alibaba Cloud services that support Resource Access Management \(RAM\), the authorization granularity and system policies for each service, and the links to related topics.

## RAM-supported Alibaba Cloud services

The following Alibaba Cloud products support RAM: [Elastic computing](#section_01), [Database](#section_02), [Storage and CDN](#section_03), [Networking](#section_04), [Analytics](#section_05), [Cloud communications](#section_06),[Management and monitoring](#section_07), [Application](#section_08), [IoT](#section_lqo_m79_230), [Message queuing](#section_nur_e8z_9qt), [Middleware](#section_09),[Media services](#section_12), [Big data](#section_13), [Security](#section_14), [Marketplace](#section_15), [Domain and hosting](#section_16), [Membership services](#section_17), [Billing management](#section_18), [Ticket services](#section_19), and [Messaging](#section_20).

For more information about the Alibaba Cloud services that support Security Token Service \(STS\), see [Alibaba Cloud services that support STS](/intl.en-US/Product Introduction/Alibaba Cloud services that support STS.md).

Each table contains the following columns:

-   Service: the name of the service that supports RAM.
-   Console: indicates whether RAM can be used to implement access control on the console of the service. A check sign \(√\) indicates that RAM is supported. A cross sign \(×\) indicates that RAM is not supported. A circle \(○\) indicates that no console is supported for the service.
-   API: indicates whether RAM can be used to implement access control on the API of the service. A check sign \(√\) indicates that RAM is supported. A cross sign \(×\) indicates that RAM is not supported. A circle \(○\) indicates that no API is provided for the service.
-   Authorization granularity: the minimum authorization granularity of the service. A hyphen \(-\) indicates that no authorization granularities are defined.

    The following authorization granularities are defined:

    -   Service: You can control whether RAM users can access the service. You can grant RAM users the permissions to access all or none of the resources in the service.
    -   Operation: You can control whether RAM users can perform specific operations on a type of resource in the service.
    -   Resource: You can control whether RAM users can perform a specific operation on a resource in the service. For example, you can authorize a RAM user to restart a specific ECS instance.
-   System policy: the system policies that RAM provides for the service. A hyphen \(-\) indicates that no system policies are provided for the service.
-   Reference: the topics that are related to both RAM and the service. A hyphen \(-\) indicates that no topics are related to RAM or the service.

## Elastic computing

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Elastic Compute Service|√|√|Resource|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[Authentication rules](/intl.en-US/API Reference/Authentication rules.md)|
|Auto Scaling|√|√|Service|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[API usage instructions](/intl.en-US/API Reference/API usage instructions.md)|
|Container Service for Kubernetes|√|√|Resource|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[Use sub-accounts](/intl.en-US/User Guide/Authorizations/Use sub-accounts.md)|
|Container Registry|√|√|Resource|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[Repository access control](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|Resource Orchestration Service|√|√|Service|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[Use RAM to control resource access](/intl.en-US/Quick Start/Use RAM to control resource access.md)|
|BatchCompute|√|√|Service|-

|-|
|Function Compute|√|√|Resource|-   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

|[Subaccount userguide](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|Elastic High Performance Computing|√|√|Service|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|Simple Application Server|√|○|Service|AliyunSWASFullAccess|-|
|Elastic Container Instance|√|√|Resource|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[Grant permissions to a RAM user](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|
|Web App Service|√|√|Operation|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|- |
|Operation Orchestration Service|√|√|Resource|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[RAM authorization policies](https://www.alibabacloud.com/help/zh/doc-detail/123024.htm)|

## Database

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|PolarDB|√|√|Operation|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[Create and authorize a RAM user](/intl.en-US/User Guide/Account Management/Create and authorize a RAM user.md)|
|ApsaraDB for RDS|√|√|Resource|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RAM authorization](/intl.en-US/API Reference/RAM authorization.md)|
|ApsaraDB for MongoDB|√|√|Resource|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|- |
|ApsaraDB for Redis|√|√|Resource|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|ApsaraDB for Memcache|√|√|Service|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|ApsaraDB for Hbase|√|√|Resource|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[Use RAM users to manage ApsaraDB for HBase clusters]()|
|Time Series Database|√|√|Operation|-

|-|
|AnalyticDB for PostgreSQL|√|√|Resource|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[Authentication rules for APIs](/intl.en-US/API Reference/Use RAM for resource authorization/Authentication rules for APIs.md)|
|AnalyticDB for MySQL|√|√|Resource|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[t1854382.dita\#multiTask1017]()|
|Data Transmission Service|√|√|Operation|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

| |
|Database Backup|√|√|Service|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|Database Autonomy Service|√|○|Service|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[How do I use a RAM user to access DAS](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|Distributed Relational Database Service|√|√|Resource|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[Use RAM for resource authorization](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
|Advanced Database & Application Migration|√|○|Service|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[t1882591.md\#]()|
|Database Gateway|√|√|Resource|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|
|LedgerDB|√|√|Resource|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[RAM user authorization]()|

## Storage and CDN

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Object Storage Service|√|√|Resource|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[Implement access control based on RAM policies](/intl.en-US/Developer Guide/Data security/Access and control/RAM Policy/Implement access control based on RAM policies.md)|
|Apsara File Storage NAS|√|○|Operation|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[Manage permission groups]()|
|Tablestore|√|√|Resource|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[Custom permissions](/intl.en-US/Developer Guide/Authorization management/Custom permissions.md)|
|Cloud Storage Gateway|√|○|Service|AliyunHCSSGWFullAccess|-|
|Hybrid Backup Recovery|√|○|Resource|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|-|
|Lightning Cube|√|○|Service|AliyunMGWFullAccess|-|
|Dynamic Route for CDN|√|√|Resource|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|CDN|√|√|Resource|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[RAM authentication](/intl.en-US/New API Reference/RAM authentication.md)|

## Networking

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Virtual Private Cloud|√|√|Resource|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|Server Load Balancer|√|√|Resource|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[RAM authentication](/intl.en-US/User Guide/Developer Guide/RAM authentication.md)|
|Elastic IP Address|√|√|Resource|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|Express Connect|√|√|Resource|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|NAT Gateway|√|√|Resource|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|VPN Gateway|√|√|Resource|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|EIP Bandwidth Plan|√|√|Resource|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|Global Accelerator|√|√|Resource|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[RAM authentication](/intl.en-US/API reference/RAM authentication.md)|
|Smart Access Gateway|√|√|Resource|-

|[RAM authentication](/intl.en-US/API Reference/RAM authentication.md)|
|Cloud Enterprise Network|√|√|Resource|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[RAM authentication]()|

## Analytics

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|E-MapReduce|√|√|Service|-   AliyunEMRFullAccess
-   AliyunEMRDevelopAccess
-   AliyunEMRFlowAdmin

|-|
|Data Lake Analytics|√|√|Operation|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

|-|

## Cloud communications

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Short Message Service|√|√|Service|-

|- |

## Management and monitoring

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Cloud Monitor|√|√|Operation|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

|[RAM for CloudMonitor](/intl.en-US/Appendix 3 account authorization/RAM for CloudMonitor.md)|
|ActionTrail|√|√|Resource|-

|[RAM authentication](/intl.en-US/API Reference/RAM account authentication.md)|
|Resource Access Management|√|√|Resource|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM authentication](/intl.en-US/API Reference (RAM)/RAM authentication.md)|
|Key Management Service|√|√|Resource|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[Use RAM to control access to resources](/intl.en-US/User Guide/Use RAM to control access to resources.md)|
|Intelligent Advisor|×|×|Operation|-|-|
|Resource Management|√|○|Resource|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[RAM authorization]()|
|Cloud Config|√|○|Service|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[Permission verification](/intl.en-US/API Reference/Permission verification.md)|

## Application

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Log Service|√|√|Resource|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[RAM authentication rules](/intl.en-US/Developer Guide/API Reference/RAM/STS/RAM authentication rules.md)|
|Direct Mail|√|√|Service|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API Gateway|√|√|Service|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[Use RAM to manage user permissions for API Gateway]()|
|Blockchain as a Service|√|√|Resource|-|[Hyperledger Fabric RAM authentication](/intl.en-US/API reference/Hyperledger Fabric RAM authentication.md)|
|Mini Program Cloud|√|√|Operation|-   AliyunMPCAFullAccess
-   AliyunMPCAReadOnlyAccess

|-|

## IoT

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|IoT Platform|√|√|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[Use RAM users](/intl.en-US/User Accounts/RAM authorization/Resource Access Management (RAM)/Use RAM users.md)|
|IoT Edge|√|√|Resource|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[Access resources of other Alibaba Cloud services](/intl.en-US/User Guide/Access resources of other Alibaba Cloud services.md)|

## Message queuing

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Message Queue for Apache RocketMQ|√|√|Resource|-   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[Grant permissions to RAM users](https://www.alibabacloud.com/help/zh/doc-detail/61382.htm)|
|Message Service|√|√|Resource|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|- |

## Middleware

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Enterprise Distributed Application Service|√|√|Service|AliyunEDASFullAccess|[Sub-accounts](https://www.alibabacloud.com/help/zh/doc-detail/44023.htm)|
|Application Real-Time Monitoring Service|√|√|Service|AliyunARMSFullAccess|[Grant different permissions to RAM users](/intl.en-US/Access control/Grant different permissions to RAM users.md)|
|Application Configuration Management|√|√|Resource|AliyunACMFullAccess|[Access control](/intl.en-US/Access Control/Access control.md)|
|Global Transaction Service|√|○|Service|-   AliyunGTSFullAccess
-   AliyunGTSReadOnlyAccess

|-|

## Media services

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|ApsaraVideo Media Processing|√|√|Service|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|[Sub-account console operating instructions](/intl.en-US/User Guide/Sub-account console operating instructions.md)|
|ApsaraVideo VOD|√|√|Service|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|ApsaraVideo Live|√|√|Resource|AliyunLiveFullAccess|[API authentication rules](/intl.en-US/API Reference/API authentication rules.md)|
|Real-Time Communication|√|√|Resource|-

|- |
|Cloud Video Conferencing|√|○|Resource|-   AliyunCVCFullAccess
-   AliyunCVCReadOnlyAccess

|-|

## Big data

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|DataWorks|√|√|Service|AliyunDataWorksFullAccess|[Use a RAM user]()|
|Quick BI|√|√|Service|-|-|
|Machine Learning Platform for AI|√|√|Service|-|-|
|Public Recognition|√|√|Service|-|-|
|DataV|√|√|Service|-|-|
|MaxCompute|√|√|Service|-|-|
|Elasticsearch|√|√|Resource|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[Resource types](/intl.en-US/RAM/Types of resources that can be authorized.md)|
|Machine Translation|×|×|Service|-|-|
|Image Search|√|√|Resource|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[Authorization policies](https://www.alibabacloud.com/help/zh/doc-detail/66586.htm)|

## Security

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Security Center|√|○|Service|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|Server Guard|√|○|Service|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|Anti-DDoS Basic|√|○|Service|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|Anti-DDoS Premium and Anti-DDoS Pro|√|○|Service|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|Anti-DDoS Premium|√|○|Service|-   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

|-|
|GameShield|√|○|Service|AliyunYundunGameShieldReadOnlyAccess

|-|
|Web Application Firewall|√|○|Service|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL Certificates Service|√|○|Service|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|Cloud Security Scanner|√|○|Service|AliyunYundunAvdsFullAccess|-|
|Content Moderation|√|○|Service|AliyunYundunGreenWebFullAccess|-|
|Anti-Bot Service|√|○|Service|-   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

|-|
|ID Verification for Financial Services|√|○|Service|-   AliyunAntCloudAuthFullAccess
-   AliyunAntCloudAuthReadOnlyAccess

|-|

## Marketplace

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Marketplace|√|○|Service|AliyunMarketplaceFullAccess|-|

## Domain and hosting

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Alibaba Cloud DNS|√|○|Resource|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|-|
|Domains|√|√|Resource|AliyunDomainFullAccess|[Authentication rules for the Domains API](/intl.en-US/Domain name management/Use RAM in Domain Name/Authentication rules for the Domains API.md)|
|Cloud Web Hosting|×|×|-|-|-|
|Alibaba Mail|×|×|-|-|-|

## Membership services

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|ICP Filing|√|○|Service|AliyunBeianFullAccess|-|

## Billing management

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Billing Management|√|×|Service|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|- |

## Ticket services

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Ticket Management|√|○|Service|AliyunSupportFullAccess|-|

## Messaging

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Message Center|√|○|Service|AliyunNotificationsFullAccess|-|

