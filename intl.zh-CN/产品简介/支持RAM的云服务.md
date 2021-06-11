# 支持RAM的云服务

本文为您介绍支持访问控制（RAM）的阿里云服务，并提供每个云服务支持的授权粒度、系统策略以及相关文档，方便您查询和使用。

## 总览

您可以按照以下分类快速查询支持RAM的云服务：

-   [弹性计算](#section_01)
-   [数据库](#section_02)
-   [存储](#section_03)
-   [云通信](#section_huy_vgm_381)
-   [网络](#section_04)
-   [运维管理](#section_0pl_xt2_475)
-   [互联网中间件](#section_d3u_2ya_hzl)
-   [视频与CDN](#section_8rc_09n_bas)
-   [企业应用](#section_vzs_r6u_os6)
-   [域名与网站](#section_do2_b0k_3um)
-   [人工智能](#section_fho_ls1_75c)
-   [IoT物联网](#section_1cu_n9s_aah)
-   [大数据](#section_13)
-   [开发者服务](#section_vl9_4wy_kja)
-   [安全](#section_14)
-   [支持与服务](#section_l28_67n_cri)
-   [云市场](#section_15)
-   [其它](#section_9k9_8u5_zca)

本文的每个表格包含以下信息：

-   云服务：支持RAM的云服务的名称。
-   子服务/子模块：云服务下的子服务或子模块。“-”表示暂无。
-   控制台：当前云服务是否支持在控制台进行访问控制，“√”表示支持，“×”表示不支持，“○”表示该云服务未接入控制台。
-   API：当前云服务是否支持通过API进行访问控制，“√”表示支持，“×”表示不支持，“○”表示该云服务未提供API。
-   授权粒度：当前云服务提供的最小授权粒度。“-”表示暂无。

    在与RAM集成时，各云服务针对RAM用户或RAM角色定义了不同级别的授权粒度：

    -   服务级别：将云服务作为一个整体进行授权。一个RAM用户或RAM角色只能处于对这个云服务拥有所有权限和没有任何权限两种状态。
    -   操作级别：API级别的授权。一个RAM用户或RAM角色可以对指定云服务的某类资源执行某几个指定的操作。
    -   资源级别：对执行资源的指定操作进行授权（最细的授权粒度）。例如：授权一个RAM用户仅可对某一台云服务器进行重启操作。
-   系统策略：当前云服务支持的系统策略。“-”表示暂无。
-   相关文档：当前云服务与RAM相关的文档链接。“-”表示暂无。

## 弹性计算

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云服务器ECS|云服务器ECS|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|块存储|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|GPU云服务器|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|弹性裸金属服务器|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|超级计算集群|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|专有宿主机|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|Alibaba Cloud Linux 2|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[云服务器ECS的鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|弹性伸缩|-|√|√|服务级别|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[弹性伸缩API使用须知](/intl.zh-CN/API参考/API使用须知.md)|
|容器服务Kubernetes版|-|√|√|资源级别|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[容器服务Kubernetes版的RAM鉴权](/intl.zh-CN/用户指南/授权管理/使用子账号.md)|
|批量计算|-|√|√|服务级别|-

|-|
|资源编排|-|√|√|服务级别|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[资源编排的RAM鉴权](/intl.zh-CN/快速入门/使用RAM控制资源访问.md)|
|函数计算|-|√|√|资源级别|-   AliyunFCFullAccess
-   AliyunFCReadOnlyAccess
-   AliyunFCInvocationAccess

|[函数计算的RAM鉴权](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|轻量应用服务器|-|√|○|服务级别|AliyunSWASFullAccess|-|
|弹性高性能计算|-|√|√|服务级别|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|容器镜像服务|-|√|√|资源级别|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[容器镜像服务的RAM鉴权](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|云桌面|弹性云桌面|√|√|资源级别|-   AliyunECDFullAccess
-   AliyunECDReadOnlyAccess
-   AliyunECDRamUserAccess

|-|
|弹性容器实例|-|√|√|资源级别|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[弹性容器实例的RAM鉴权](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|
|Serverless工作流|-|√|√|资源级别|-   AliyunFnFFullAccess
-   AliyunFnFReadOnlyAccess

|[Serverless工作流的RAM鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|Web应用托管服务|-|√|√|操作级别|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|- |

## 数据库

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|关系型数据库|关系型数据库|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库MySQL版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库SQL Server版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库PostgreSQL版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库PPAS版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库专属集群|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|-|
|云数据库Redis版|-|√|√|资源级别|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[Redis的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|云数据库Memcache版|-|√|√|服务级别|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|云数据库MongoDB版|-|√|√|资源级别|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|- |
|云原生数据仓库ADB PostgreSQL版|-|√|√|资源级别|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[云原生数据仓库ADB PostgreSQL版的RAM鉴权](/intl.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md)|
|数据传输|-|√|√|操作级别|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

|[数据传输的RAM鉴权](/intl.zh-CN/RAM授权管理/通过系统策略授权子账号管理DTS.md)|
|数据管理|-|√|√|服务级别|-|- |
|云原生数据仓库ADB MySQL版|-|√|√|操作级别|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[云原生数据仓库ADB MySQL版的RAM鉴权](云原生数据仓库ADB MySQL版的RAM鉴权t1854382.dita#multiTask1017)|
|云原生分布式数据库 PolarDB-X|-|√|√|资源级别|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[DRDS支持的资源授权](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
|云数据库HBase版|-|√|√|资源级别|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[HBase的RAM鉴权]()|
|数据库和应用迁移|-|√|○|服务级别|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[数据库和应用迁移的RAM鉴权]()|
|云原生关系型数据库PolarDB|-|√|√|操作级别|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[PolarDB的RAM鉴权](/intl.zh-CN/用户指南/账号和数据库/创建和管理RAM用户.md)|
|数据库备份|-|√|√|服务级别|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|数据库自治服务|-|√|√|服务级别|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[RAM用户如何使用DAS](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|云原生数据湖分析|-|√|√|操作级别|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess
-   AliyunDLADeveloperAccess

|[授予RAM账号细粒度访问DLA的权限]()|
|云数据库OceanBase|-|√|○|服务级别|-   AliyunOceanBaseFullAccess
-   AliyunOceanBaseReadOnlyAccess

|-|
|云数据库Cassandra版|-|√|√|资源级别|-   AliyunCassandraFullAccess
-   AliyunCassandraReadOnlyAccess

|[Cassandra的RAM鉴权]()|
|可信账本数据库|-|√|√|资源级别|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[可信账本数据库的RAM鉴权]()|
|云数据库ClickHouse|-|√|√|资源级别|-   AliyunClickHouseFullAccess
-   AliyunClickHouseReadOnlyAccess

|[ClickHouse RAM鉴权]()|
|数据库网关DG|-|√|√|资源级别|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|

## 存储

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|对象存储|-|√|√|资源级别|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[对象存储RAM鉴权](/intl.zh-CN/开发指南/数据安全/访问控制/RAM Policy/RAM Policy概述.md)|
|文件存储NAS|-|√|√|操作级别|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[使用RAM权限策略控制NAS访问权限]()|
|表格存储|-|√|√|资源级别|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[表格存储RAM鉴权](/intl.zh-CN/功能介绍/授权管理/自定义权限.md)|
|云存储网关|-|√|√|服务级别|AliyunHCSSGWFullAccess|[云存储网关的RAM鉴权](/intl.zh-CN/最佳实践/账号访问控制.md)|
|混合云备份服务|-|√|○|资源级别|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|[用户权限管理](/intl.zh-CN/最佳实践/用户权限管理.md)|
|混合云存储|-|×|○|-|-|-|

## 云通信

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|短信服务|-|√|√|服务级别|-

|- |

## 网络

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|专有网络VPC|-|√|√|资源级别|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[VPC的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|负载均衡|负载均衡|√|√|资源级别|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[SLB的RAM鉴权](/intl.zh-CN/传统型负载均衡CLB/CLB开发指南/API参考/RAM鉴权.md)|
|负载均衡|应用型负载均衡|√|√|资源级别|-   AliyunALBFullAccess
-   AliyunALBReadOnlyAccess

|-|
|高速通道|-|√|√|资源级别|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[高速通道的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|弹性公网IP|-|√|√|资源级别|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[EIP的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|NAT网关|-|√|√|资源级别|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[NAT网关的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|VPN网关|-|√|√|资源级别|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[VPN网关的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|共享带宽|-|√|√|资源级别|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|全球加速|-|√|√|资源级别|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[全球加速的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|智能接入网关|-|√|√|资源级别|-

|[智能接入网关的RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|云企业网|-|√|√|资源级别|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[云企业网的RAM鉴权]()|
|私网连接|-|√|√|资源级别|-   AliyunPrivateLinkFullAccess
-   AliyunPrivateLinkReadOnlyAccess

|-   [使用RAM对私网连接进行权限管理]()
-   [私网连接的RAM鉴权]() |
|云解析PrivateZone|-|√|√|资源级别|-   AliyunPvtzFullAccess
-   AliyunPvtzReadOnlyAccess

|[云解析PrivateZone的RAM鉴权](https://www.alibabacloud.com/help/doc-detail/65886.htm)|

## 运维管理

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|应用实时监控服务|-|√|√|服务级别|-   AliyunARMSFullAccess
-   AliyunARMSReadOnlyAccess

|[ARMS的RAM鉴权](/intl.zh-CN/访问控制/借助RAM用户实现分权.md)|
|云监控|-|√|√|操作级别|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess
-   AliyunCloudMonitorMetricDataReadOnlyAccess

|[云监控的RAM鉴权](/intl.zh-CN/附录3 账号授权相关/访问控制.md)|
|云命令行|-|√|○|服务级别|-|-|
|配置审计|-|√|√|服务级别|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|逻辑编排|-|√|√|资源级别|-   AliyunLogicComposerFullAccess
-   AliyunLogicComposerReadOnlyAccess

|[逻辑编排的RAM鉴权]()|
|运维编排服务|-|√|√|资源级别|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[OOS的RAM鉴权]()|

## 互联网中间件

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|企业级分布式应用服务|-|√|√|服务级别|-   AliyunEDASFullAccess
-   AliyunEDASReadOnlyAccess
-   AliyunEDASApplicationFullAccess
-   AliyunEDASApplicationReadOnlyAccess
-   AliyunEDASResourceReadOnlyAccess
-   AliyunEDASResourceFullAccess

|[EDAS的RAM鉴权]()|
|消息队列MQ|消息队列Rocket MQ版|√|√|资源级别|-   AliyunMQFullAccess
-   AliyunMQReadOnlyAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[消息队列Rocket MQ版的RAM鉴权]()|
|消息队列MQ|微消息队列MQTT版|√|√|资源级别|-   AliyunMQFullAccess
-   AliyunMQReadOnlyAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[微消息队列MQTT版的RAM鉴权]()|
|消息队列MQ|消息队列RabbitMQ版|√|√|资源级别|-   AliyunAMQFullAccess
-   AliyunAMQPReadOnlyAccess

|[消息队列RabbitMQ版的RAM鉴权]()|
|消息服务|-|√|√|资源级别|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|[消息服务的RAM鉴权](消息服务的RAM鉴权t1835681.dita#task810)|
|应用配置管理|-|√|√|资源级别|AliyunACMFullAccess|[应用配置管理的RAM鉴权](/intl.zh-CN/访问控制/访问权限控制.md)|
|消息队列Kafka版|-|√|√|服务级别|-   AliyunKafkaFullAccess
-   AliyunKafkaReadOnlyAccess

|[消息队列Kafka版的RAM鉴权](/intl.zh-CN/权限控制/RAM主子账号授权.md)|
|应用高可用服务|-|√|√|服务级别|-   AliyunAHASFullAccess
-   AliyunAHASReadOnlyAccess

|- |
|服务网格|-|√|√|资源级别|-|[服务网格的RAM鉴权](https://www.alibabacloud.com/help/doc-detail/169466.htm)|
|事件总线|-|√|√|资源级别|-   AliyunEventBridgeFullAccess
-   AliyunEventBridgeReadOnlyAccess
-   AliyunEventBridgeResourceCreatePolicy
-   AliyunEventBridgeResourceDeletePolicy
-   AliyunEventBridgeResourceUpdatePolicy
-   AliyunEventBridgePutEventsPolicy

|[事件总线的RAM鉴权]()|

## 视频与CDN

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|CDN|-|√|√|资源级别|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[CDN的RAM鉴权](/intl.zh-CN/新版API参考/RAM鉴权.md)|
|媒体处理|-|√|√|服务级别|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|- |
|视频点播|-|√|√|操作级别|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|视频直播|-|√|√|资源级别|-   AliyunLiveFullAccess
-   AliyunLiveReadOnlyAccess

|[视频直播的RAM鉴权](/intl.zh-CN/API参考/API鉴权规则.md)|
|音视频通信|-|√|√|资源级别|-

|- |
|全站加速|-|√|√|资源级别|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|

## 企业应用

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|邮件推送|-|√|√|服务级别|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API网关|-|√|√|服务级别|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[API网关的RAM鉴权]()|
|资源管理|资源管理|√|√|操作级别|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[资源目录的RAM鉴权]()|
|资源管理|标签|√|√|操作级别|-   AliyunTAGFullAccess
-   AliyunTAGReadOnlyAccess

|[标签鉴权列表](section_zqv_es3_ege)|
|区块链服务|区块链服务|√|√|资源级别|-   AliyunBaaSFullAccess
-   AliyunBaaSReadOnlyAccess

|[Hyperledger Fabric RAM鉴权](/intl.zh-CN/API参考/Hyperledger Fabric RAM鉴权.md)|
|云行情|-|√|○|服务级别|-   AliyunCQLoudFullAccess
-   AliyunCQLoudReadOnlyAccess

|-|

## 域名与网站

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云解析DNS|云解析DNS|√|√|资源级别|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|- |
|云解析DNS|公共DNS|√|√|资源级别|-   AliyunPubDNSReadOnlyAccess
-   AliyunPubDNSFullAccess

|-|
|域名|-|√|√|资源级别|AliyunDomainFullAccess|[域名的RAM鉴权](/intl.zh-CN/域名管理/RAM资源授权-域名/Domain API鉴权规则.md)|

## 人工智能

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|智能语音交互|-|√|√|服务级别|-   AliyunNLSFullAccess
-   AliyunNLSReadOnlyAccess

|-|
|机器学习|-|√|√|服务级别|-|-|
|图像搜索|-|√|√|资源级别|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[图像搜索的RAM鉴权](https://www.alibabacloud.com/help/zh/doc-detail/179180.htm)|
|机器翻译|-|√|√|服务级别|-|-|

## IoT物联网

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|物联网平台|-|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[物联网平台的RAM鉴权](/intl.zh-CN/账号与登录/账号授权/RAM授权管理/RAM用户访问.md)|
|物联网边缘计算|-|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[物联网边缘计算的RAM鉴权](/intl.zh-CN/物联网边缘计算/用户指南/云资源访问.md)|
|云原生多模数据库Lindorm|时序数据库TSDB|√|√|操作级别|-

|-|

## 大数据

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|DataWorks|-|√|√|服务级别|AliyunDataWorksFullAccess|[DataWorks的RAM鉴权]()|
|Quick BI|-|√|√|服务级别|-|-|
|DataV数据可视化|-|√|○|服务级别|AliyunDataVFullAccess|-|
|实时计算Flink版|-|√|√|服务级别|-|-|
|Elasticsearch|-|√|√|资源级别|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[Elasticsearch的RAM鉴权](/intl.zh-CN/访问控制/授权资源类型.md)|
|E-MapReduce|-|√|√|服务级别|-   AliyunEMRFullAccess
-   AliyunUEMReadOnlyAccess
-   AliyunEMRFlowAdmin
-   AliyunEMRDevelopAccess

|-|
|日志服务|-|√|√|资源级别|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[日志服务的RAM鉴权](/intl.zh-CN/开发指南/API参考/RAM/STS/鉴权规则.md)|
|交互式分析|-|√|√|资源级别|-   AliyunHologresFullAccess
-   AliyunHologresReadOnlyAccess

|[RAM用户使用Hologres快速入门](/intl.zh-CN/快速入门/RAM用户使用Hologres快速入门.md)|

## 开发者服务

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云效|-|√|√|资源级别|-   AliyunRDCFullAccess
-   AliyunRDCReadOnlyAccess

|-|
|链路追踪|-|√|√|服务级别|-   AliyunTracingAnalysisFullAccess
-   AliyunTracingAnalysisReadOnlyAccess

|-|

## 安全

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云安全中心（态势感知）|-|√|√|服务级别|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|云安全中心（安骑士）|-|√|√|服务级别|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|DDoS防护|DDoS防护|√|√|服务级别|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|DDoS防护|DDoS高防|√|√|服务级别|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|DDoS防护|DDoS高防（国际）|√|○|服务级别|-   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

|-|
|游戏盾|-|√|○|服务级别|AliyunYundunGameShieldReadOnlyAccess

|-|
|Web应用防火墙|Web应用防火墙|√|√|服务级别|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL证书|-|√|√|服务级别|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|云防火墙|-|√|√|服务级别|-   AliyunYundunCloudFirewallReadOnlyAccess
-   AliyunYundunCloudFirewallFullAccess

|-|
|安全管家|-|√|○|服务级别|-|-|
|内容安全|-|√|√|服务级别|AliyunYundunGreenWebFullAccess|-|
|堡垒机|堡垒机|√|○|服务级别|-   AliyunYundunBastionHostFullAccess
-   AliyunYundunBastionHostReadOnlyAccess
-   AliyunYundunBastionHostOperateOnlyAccess
-   AliyunYundunBastionHostAuditOnlyAccess

|-|
|数据安全中心|-|√|√|服务级别|-   AliyunYundunSDDPFullAccess
-   AliyunYundunSDDPReadOnlyAccess

|-|
|应用身份服务IDaaS|-|√|○|操作级别|-   AliyunYundunIdaasFullAccess
-   AliyunYundunIdaasReadOnlyAccess

|-|
|密钥管理服务|-|√|√|资源级别|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[使用RAM实现对资源的访问控制](/intl.zh-CN/访问控制与审计/使用RAM实现对资源的访问控制.md)|
|访问控制|-|√|√|资源级别|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/API参考（RAM）/RAM鉴权.md)|
|操作审计|-|√|√|操作级别|-

|[操作审计的RAM鉴权](/intl.zh-CN/API参考/API参考（2017-12-04）（不推荐）/RAM鉴权.md)|

## 支持与服务

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|工单|-|√|√|服务级别|AliyunSupportFullAccess|-|

## 云市场

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云市场|-|√|×|服务级别|AliyunMarketplaceFullAccess|-|

## 其它

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|费用中心|-|√|√|服务级别|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess
-   AliyunBSSRenewReadOnlyAccess
-   AliyunBSSRenewFullAccess

|- |
|备案|-|√|○|服务级别|AliyunBeianFullAccess|-|

