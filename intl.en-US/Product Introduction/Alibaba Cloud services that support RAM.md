# Alibaba Cloud services that support RAM

This topic lists the Alibaba Cloud services that support Resource Access Management \(RAM\), the authorization granularity and system policies for each service, and the links to related topics.

## Services that support RAM

The following types of services support RAM: [elastic computing](#section_01), [database](#section_02), [storage and CDN](#section_03), [networking](#section_04), [analysis](#section_05), [cloud communications](#section_06), [monitoring and management](#section_07), [application](#section_08), [Internet of Things \(IoT\)](#section_lqo_m79_230), [message queuing](#section_nur_e8z_9qt), [middleware](#section_09), [media](#section_12), [big data](#section_13), [security](#section_14), [marketplace](#section_15), [domain and website](#section_16), [membership](#section_17), [billing management](#section_18), [support](#section_19), and [messaging](#section_20).

For more information about the list of Alibaba Cloud services that support Security Token Service \(STS\), see [Alibaba Cloud services that support STS](/intl.en-US/Product Introduction/Alibaba Cloud services that support STS.md).

Each table contains the following columns:

-   Service: the service name.
-   Console: indicates whether RAM can be used to implement access control on the console of the service. A check sign \(√\) indicates that RAM can be used to implement the access control. A cross sign \(×\) indicates that RAM cannot be used to implement the access control. A circle \(○\) indicates that no console is available for the service.
-   API: indicates whether RAM can be used to implement access control on the API of the service. A check sign \(√\) indicates that RAM can be used to implement the access control. A cross sign \(×\) indicates that RAM cannot be used to implement the access control. A circle \(○\) indicates that the service does not provide an API.
-   Authorization granularity: the minimum authorization granularity of the service. A hyphen \(-\) indicates that no authorization granularities are defined.

    The following authorization granularities are available:

    -   Service: You can control whether RAM users can access the service. You can grant RAM users the permissions to access all or none of the service resources.
    -   Operation: You can control whether RAM users can perform specific operations on a type of service resource.
    -   Resource: You can control whether RAM users can perform a specific operation on a service resource. For example, you can authorize a RAM user to restart a specific ECS instance.
-   System policy: the system policies that RAM provides for the service. A hyphen \(-\) indicates that no system policies are available.
-   Reference: the topics that are related to both RAM and the service. A hyphen \(-\) indicates that no topics are available.

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
|Alibaba Cloud Container Service for Kubernetes|√|√|Resource|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[Use sub-accounts](/intl.en-US/User Guide/Authorizations/Use sub-accounts.md)|
|Container Registry|√|√|Resource|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[Repository access control](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|Resource Orchestration Service|√|√|Service|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[Use RAM to control resource access](/intl.en-US/Quick Start/Use RAM to control resource access.md)|
|Batch Compute|√|√|Service|-

|-|
|Function Compute|√|√|Resource|-   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

|[Subaccount userguide](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|E-HPC|√|√|Service|-   AliyunEHPCFullAccess
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

|[RAM authorization](/intl.en-US/API Reference/RAM authentication.md)|
|ApsaraDB for Memcache|√|√|Service|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|ApsaraDB for Hbase|√|√|Resource|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[Use RAM users to manage ApsaraDB for HBase clusters]()|
|Time Series Database \(TSDB\)|√|√|Operation|-

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

|[What can I do if I fail to access DAS as a RAM user due to lack of permissions?](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|Distributed Relational Database Service|√|√|Resource|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[Support for RAM authorization](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
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
|Data Transport|√|○|Service|AliyunMGWFullAccess|-|
|Dynamic Route for CDN|√|√|Resource|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|Alibaba Cloud CDN|√|√|Resource|-   AliyunCDNFullAccess
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

## Analysis

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

## Monitoring and management

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Cloud Monitor|√|√|Operation|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

|[RAM for CloudMonitor](/intl.en-US/Appendix 3 account authorization/RAM for CloudMonitor.md)|
|ActionTrail|√|√|Resource|-

|[RAM account authentication](/intl.en-US/API Reference/RAM account authentication.md)|
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

|[Authentication rules](/intl.en-US/Developer Guide/API Reference/RAM/STS/RAM authentication rules.md)|
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
|Alibaba Cloud Message Queue for Apache RocketMQ|√|√|Resource|-   AliyunMQFullAccess
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

## Media

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|ApsaraVideo for Media Processing|√|√|Service|-   AliyunMTSFullAccess
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
|DataWorks|√|√|Service|AliyunDataWorksFullAccess|[RAM User Operations]()|
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

|[Authorization policies](https://www.alibabacloud.com/help/doc-detail/179180.htm)|

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
|Anti-DDoS Pro|√|○|Service|-   AliyunYundunHighFullAccess
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
|Alibaba Cloud Marketplace|√|○|Service|AliyunMarketplaceFullAccess|-|

## Domain and website

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Alibaba Cloud DNS|√|○|Resource|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|-|
|Domains|√|√|Resource|AliyunDomainFullAccess|[Domain API Authentication Rules](/intl.en-US/Domain name management/Use RAM in Domain Name/Authentication rules for the Domains API.md)|
|Cloud Web Hosting|×|×|-|-|-|
|Alibaba Mail|×|×|-|-|-|

## Membership

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|ICP Filing|√|○|Service|AliyunBeianFullAccess|-|

## Billing Management

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Billing Management|√|×|Service|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|- |

## Support

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Ticket Management|√|○|Service|AliyunSupportFullAccess|-|

## Messaging

|Service|Console|API|Authorization granularity|System policy|Reference|
|:------|:------|:--|:------------------------|:------------|:--------|
|Message Center|√|○|Service|AliyunNotificationsFullAccess|-|

