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
-   [移动云](#section_84e_f0c_j5i)
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

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|块存储|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|GPU云服务器|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|弹性裸金属服务器|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|超级计算集群|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|专有宿主机|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|云服务器ECS|Alibaba Cloud Linux 2|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess

|[云服务器ECS的鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|弹性伸缩|-|√|√|服务级别|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[弹性伸缩API使用须知](/cn.zh-CN/API参考/API使用须知.md)|
|容器服务|-|√|√|资源级别|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|-|
|容器服务Kubernetes版|-|√|√|资源级别|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[容器服务Kubernetes版的RAM鉴权](/cn.zh-CN/用户指南/授权管理/使用子账号.md)|
|批量计算|-|√|√|服务级别|AliyunBatchComputeFullAccess

|-|
|资源编排|-|√|√|服务级别|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[资源编排的RAM鉴权](/cn.zh-CN/快速入门/使用RAM控制资源访问.md)|
|函数计算|-|√|√|资源级别|-   AliyunFCFullAccess
-   AliyunFCReadOnlyAccess
-   AliyunFCInvocationAccess

|[函数计算的RAM鉴权](https://help.aliyun.com/document_detail/55617.html)|
|轻量应用服务器|-|√|○|服务级别|AliyunSWASFullAccess|-|
|弹性高性能计算|-|√|√|服务级别|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|容器镜像服务|-|√|√|资源级别|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[容器镜像服务的RAM鉴权](https://help.aliyun.com/document_detail/67992.html)|
|云桌面|云桌面|√|○|服务级别|AliyunGwsFullAccess|-|
|云桌面|弹性云桌面|√|√|操作级别|-   AliyunECDFullAccess
-   AliyunECDReadOnlyAccess
-   AliyunECDRamUserAccess

|-|
|弹性容器实例|-|√|√|资源级别|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[弹性容器实例的RAM鉴权](https://help.aliyun.com/document_detail/92790.html)|
|Serverless工作流|-|√|√|资源级别|-   AliyunFnFFullAccess
-   AliyunFnFReadOnlyAccess

|[Serverless工作流的RAM鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|Web应用托管服务|-|√|√|操作级别|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|[Web应用托管服务的RAM鉴权](/cn.zh-CN/访问控制/借助 RAM 用户实现分权.md)|
|弹性加速计算实例|-|√|√|资源级别|-   AliyunEAISFullAccess
-   AliyunEAISReadOnlyAccess

|-|
|云盒|-|√|○|资源级别|-   AliyunCloudBoxFullAccess
-   AliyunCloudBoxReadOnlyAccess

|-|

## 数据库

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|关系型数据库|关系型数据库|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库MySQL版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库SQL Server版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库PostgreSQL版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库PPAS版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RDS的RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|关系型数据库|云数据库专属集群|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|-|
|云数据库Redis版|-|√|√|资源级别|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[Redis的RAM鉴权](/cn.zh-CN/API与SDK参考/API参考/RAM鉴权.md)|
|云数据库Memcache版|-|√|√|服务级别|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|云数据库MongoDB版|-|√|√|资源级别|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|[MongoDB的RAM鉴权](/cn.zh-CN/API参考/如何使用RAM授权/MongoDB API的鉴权规则.md)|
|云原生数据仓库ADB PostgreSQL版|-|√|√|资源级别|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[云原生数据仓库ADB PostgreSQL版的RAM鉴权](/cn.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md)|
|HybridDB for MySQL（已下线）|-|√|√|资源级别|-   AliyunPetaDataFullAccess
-   AliyunPetaDataReadOnlyAccess

|-|
|数据传输|-|√|√|操作级别|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

|[数据传输的RAM鉴权](/cn.zh-CN/访问控制/通过系统策略授权子账号管理DTS.md)|
|数据管理|-|√|√|服务级别|-|[数据管理资源授权](https://help.aliyun.com/document_detail/47571.html)|
|云原生数据仓库ADB MySQL版|-|√|√|操作级别|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[云原生数据仓库ADB MySQL版的RAM鉴权](云原生数据仓库ADB MySQL版的RAM鉴权t1854382.dita#multiTask1017)|
|云原生分布式数据库 PolarDB-X|-|√|√|资源级别|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[PolarDB-X支持的资源授权](https://help.aliyun.com/document_detail/51480.html)|
|云数据库HBase版|-|√|√|资源级别|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[HBase的RAM鉴权]()|
|数据库和应用迁移|-|√|○|服务级别|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[数据库和应用迁移的RAM鉴权]()|
|云原生关系型数据库PolarDB|-|√|√|操作级别|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[PolarDB的RAM鉴权](/cn.zh-CN/用户指南/账号和数据库/创建和管理RAM用户.md)|
|数据库备份|-|√|√|服务级别|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|数据库自治服务|-|√|√|服务级别|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[RAM用户如何使用DAS](https://help.aliyun.com/knowledge_detail/66674.html)|
|云原生数据湖分析|-|√|√|操作级别|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess
-   AliyunDLADeveloperAccess

|[授予RAM账号细粒度访问DLA的权限]()|
|图数据库|-|√|√|资源级别|-   AliyunGDBFullAccess
-   AliyunGDBReadOnlyAccess

|[图数据库的RAM鉴权]()|
|数据库专家服务|-|√|○|服务级别|AliyunDBESFullAccess|-|
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

|[对象存储RAM鉴权](/cn.zh-CN/开发指南/数据安全/访问控制/RAM Policy/RAM Policy概述.md)|
|文件存储NAS|-|√|√|操作级别|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[使用RAM权限策略控制NAS访问权限]()|
|表格存储|-|√|√|资源级别|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[表格存储RAM鉴权](/cn.zh-CN/功能介绍/授权管理/自定义权限.md)|
|云存储网关|-|√|√|服务级别|AliyunHCSSGWFullAccess|[云存储网关的RAM鉴权](/cn.zh-CN/最佳实践/账号访问控制.md)|
|智能云相册|-|√|√|资源级别|-   AliyunCloudPhotoFullAccess
-   AliyunCloudPhotoReadOnlyAccess

|[授权映射表](https://help.aliyun.com/document_detail/56485.html)|
|混合云备份服务|-|√|○|资源级别|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|[用户权限管理](/cn.zh-CN/最佳实践/用户权限管理.md)|
|混合云容灾服务|-|√|○|服务级别|AliyunHDRFullAccess|[混合云容灾服务的RAM鉴权](https://help.aliyun.com/document_detail/144767.html)|
|智能媒体管理|-|√|√|服务级别|-   AliyunIMMReadOnlyAccess
-   AliyunIMMFullAccess

|[智能媒体管理RAM鉴权](https://help.aliyun.com/document_detail/73265.html)|
|文件存储HDFS|-|√|√|资源级别|-   AliyunHDFSFullAccess
-   AliyunHDFSReadOnlyAccess

|[使用RAM授权访问](/cn.zh-CN/用户指南/使用RAM授权访问.md)|
|数据库文件存储|-|√|√|资源级别|-   AliyunDBFSFullAccess
-   AliyunDBFSReadOnlyAccess

|[数据库文件存储的RAM鉴权](https://help.aliyun.com/document_detail/160141.html)|
|相册与网盘服务|-|√|√|资源级别|-   AliyunPDSFullAccess
-   AliyunPDSReadOnlyAccess

|-|
|归档存储|-|×|○|-|-|-|
|混合云存储|-|×|○|-|-|-|
|闪电立方|-|√|○|服务级别|AliyunMGWFullAccess|-|
|内容协作平台|-|√|√|服务级别|-   AliyunCCPFullAccess
-   AliyunCCPReadOnlyAccess

|-|

## 云通信

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|短信服务|-|√|√|服务级别|-   AliyunDysmsFullAccess
-   AliyunDysmsReadOnlyAccess

|[短信服务RAM鉴权](https://help.aliyun.com/document_detail/108069.html)|
|流量服务|-|√|√|服务级别|-   AliyunDycdpFullAccess
-   AliyunDycdpReadOnlyAccess

|-|
|语音服务|-|√|√|服务级别|-   AliyunDyvmsFullAccess
-   AliyunDyvmsReadOnlyAccess

|[语音权限访问控制](https://help.aliyun.com/document_detail/55766.html)|
|号码隐私保护|-|√|√|服务级别|-   AliyunDyplsFullAccess
-   AliyunDyplsReadOnlyAccess

|[号码权限访问控制](https://help.aliyun.com/document_detail/59872.html)|
|号码认证服务|-|√|√|服务级别|-   AliyunDypnsFullAccess
-   AliyunDypnsReadOnlyAccess

|[号码认证服务的RAM鉴权](https://help.aliyun.com/document_detail/88440.html)|
|云通信网络加速|-|√|√|操作级别|-   AliyunSNSUFullAccess
-   AliyunSNSUReadOnlyAccess

|-|
|智能联络中心|-|√|○|资源级别|-   AliyunAiccsFullAccess
-   AliyunAiccsReadOnlyAccess

|-|
|云会议|-|√|○|资源级别|-   AliyunCVCFullAccess
-   AliyunCVCReadOnlyAccess

|-|
|号码百科|-|√|√|操作级别|-   AliyunDytnsFullAccess
-   AliyunDytnsReadOnlyAccess

|[号码百科RAM鉴权](https://help.aliyun.com/document_detail/154006.html?spm=a2c4g.11186623.6.551.4f505a58fSwtZC)|

## 网络

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|专有网络VPC|-|√|√|资源级别|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[VPC的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|负载均衡|负载均衡|√|√|资源级别|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[SLB的RAM鉴权](/cn.zh-CN/传统型负载均衡CLB/CLB开发指南/API参考/RAM鉴权.md)|
|负载均衡|应用型负载均衡|√|√|资源级别|-   AliyunALBFullAccess
-   AliyunALBReadOnlyAccess

|-|
|高速通道|-|√|√|资源级别|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[高速通道的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|弹性公网IP|-|√|√|资源级别|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[EIP的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|共享流量包|-|√|○|服务级别|-|-|
|NAT网关|-|√|√|资源级别|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[NAT网关的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|VPN网关|-|√|√|资源级别|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[VPN网关的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|共享带宽|-|√|√|资源级别|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|全球加速|-|√|√|资源级别|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[全球加速的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|智能接入网关|-|√|√|资源级别|-   AliyunSmartAccessGatewayFullAccess
-   AliyunSmartAccessGatewayReadOnlyAccess

|[智能接入网关的RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|IPv6转换服务|-|√|√|资源级别|-   AliyunIPv6TranslationFullAccess
-   AliyunIPv6TranslationReadOnlyAccess

|-|
|云企业网|-|√|√|资源级别|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[云企业网的RAM鉴权]()|
|私网连接|-|√|√|资源级别|-   AliyunPrivateLinkFullAccess
-   AliyunPrivateLinkReadOnlyAccess

|-   [使用RAM对私网连接进行权限管理]()
-   [私网连接的RAM鉴权]() |
|云解析PrivateZone|-|√|√|资源级别|-   AliyunPvtzFullAccess
-   AliyunPvtzReadOnlyAccess

|[云解析PrivateZone的RAM鉴权](https://help.aliyun.com/document_detail/65886.html)|
|云托付|-|×|○|-|-|-|

## 运维管理

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|应用实时监控服务|-|√|√|服务级别|-   AliyunARMSFullAccess
-   AliyunARMSReadOnlyAccess

|[ARMS的RAM鉴权](/cn.zh-CN/访问控制/借助RAM用户实现分权.md)|
|云监控|-|√|√|操作级别|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess
-   AliyunCloudMonitorMetricDataReadOnlyAccess

|[云监控的RAM鉴权](/cn.zh-CN/附录3 账号授权相关/访问控制.md)|
|智能顾问|-|√|√|操作级别|-   AliyunAdvisorFullAccess
-   AliyunAdvisorReadOnlyAccess

|-|
|OpenAPI Explorer|OpenAPI Explorer|√|○|服务级别|-|-|
|OpenAPI Explorer|IaC服务|√|√|资源级别|-   AliyunIaCServiceFullAccess
-   AliyunIaCServiceReadOnlyAccess

|-|
|云命令行|-|√|○|服务级别|-|-|
|配置审计|-|√|√|服务级别|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|逻辑编排|-|√|√|资源级别|-   AliyunLogicComposerFullAccess
-   AliyunLogicComposerReadOnlyAccess

|[逻辑编排的RAM鉴权]()|
|运维编排服务|-|√|√|资源级别|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[OOS的RAM鉴权]()|
|云网管|-|√|√|资源级别|-   AliyunCMNFullAccess
-   AliyunCMNReadOnlyAccess

|[云网管的RAM鉴权]()|

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
|云服务总线CSB|-|√|√|资源级别|AliyunCSBFullAccess|[如何为RAM用户授权使用CSB]()|
|性能测试|-|√|√|服务级别|AliyunPTSFullAccess|-|
|消息服务|-|√|√|资源级别|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|[消息服务的RAM鉴权](消息服务的RAM鉴权t1835681.dita#task810)|
|应用配置管理|-|√|√|资源级别|AliyunACMFullAccess|[应用配置管理的RAM鉴权](/cn.zh-CN/访问控制/访问权限控制.md)|
|消息队列Kafka版|-|√|√|服务级别|-   AliyunKafkaFullAccess
-   AliyunKafkaReadOnlyAccess

|[消息队列Kafka版的RAM鉴权](/cn.zh-CN/访问控制（权限管理）/RAM主子账号授权.md)|
|应用高可用服务|-|√|√|服务级别|-   AliyunAHASFullAccess
-   AliyunAHASReadOnlyAccess

|[应用高可用服务的RAM鉴权](/cn.zh-CN/权限管理/访问控制概述.md)|
|Serverless应用引擎|-|√|√|服务级别|-   AliyunSAEFullAccess
-   AliyunSAEReadOnlyAccess

|[Serverless应用引擎的RAM鉴权](/cn.zh-CN/权限管理/权限策略和示例.md)|
|服务网格|-|√|√|资源级别|-|[服务网格的RAM鉴权](https://help.aliyun.com/document_detail/169466.html)|
|事件总线|-|√|√|资源级别|-   AliyunEventBridgeFullAccess
-   AliyunEventBridgeReadOnlyAccess
-   AliyunEventBridgeResourceCreatePolicy
-   AliyunEventBridgeResourceDeletePolicy
-   AliyunEventBridgeResourceUpdatePolicy
-   AliyunEventBridgePutEventsPolicy

|[事件总线的RAM鉴权]()|
|全局事务服务|-|√|√|服务级别|-   AliyunGTSFullAccess
-   AliyunGTSReadOnlyAccess

|[为RAM用户授权事务分组](/cn.zh-CN/最佳实践/为 RAM 用户授权事务分组.md)|

## 视频与CDN

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|CDN|-|√|√|资源级别|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[CDN的RAM鉴权](/cn.zh-CN/新版API参考/RAM鉴权.md)|
|媒体处理|-|√|√|服务级别|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|[媒体处理的RAM鉴权](/cn.zh-CN/用户指南/权限管理/RAM用户使用控制台说明.md)|
|视频点播|-|√|√|操作级别|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|视频直播|-|√|√|资源级别|-   AliyunLiveFullAccess
-   AliyunLiveReadOnlyAccess

|[视频直播的RAM鉴权](/cn.zh-CN/API参考/API鉴权规则.md)|
|音视频通信|-|√|√|资源级别|-   AliyunRTCFullAccess
-   AliyunRTCReadOnlyAccess

|[音视频通信RAM鉴权](https://help.aliyun.com/document_detail/74559.html)|
|智能视觉|-|√|√|操作级别|-   AliyunIVisionFullAccess
-   AliyunIVisionReadOnlyAccess

|-|
|视频监控|-|√|√|操作级别|-   AliyunVSFullAccess
-   AliyunVSReadOnlyAccess

|-|
|PCDN|-|√|√|资源级别|-   AliyunPCDNFullAccess
-   AliyunPCDNReadOnlyAccess

|[PCDN的RAM鉴权](https://help.aliyun.com/document_detail/58028.html)|
|全站加速|-|√|√|资源级别|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|安全加速SCDN|-|√|√|资源级别|-   AliyunSCDNReadOnlyAccess
-   AliyunSCDNFullAccess

|-|
|边缘节点服务ENS|-|√|√|资源级别|-   AliyunENSReadOnlyAccess
-   AliyunENSFullAccess

|-|
|智能媒体生产|-|√|√|资源级别|-   AliyunICEFullAccess
-   AliyunICEReadOnlyAccess

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
|阿里邮箱|-|×|×|-|-|-|
|云AP|-|×|×|-|-|-|
|机器人流程自动化|-|×|×|-|-|-|
|云投屏|-|√|○|服务级别|AliyunWorkSuiteCDFullAccess|-|
|资源管理|资源管理|√|√|操作级别|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[资源目录的RAM鉴权]()|
|资源管理|标签|√|√|操作级别|-   AliyunTAGFullAccess
-   AliyunTAGReadOnlyAccess

|[标签鉴权列表]()|
|智能对话分析|-|√|√|资源级别|-   AliyunSCAFullAccess
-   AliyunSCAReadOnlyAccess

|-|
|智能对话机器人|-|√|√|服务级别|AliyunChatbotFullAccess|-|
|云呼叫中心|云呼叫中心|√|√|服务级别|AliyunCCCFullAccess|-|
|云呼叫中心|智能语音导航|√|√|操作级别|-   AliyunVoiceNavigatorFullAccess
-   AliyunVoiceNavigatorReadOnlyAccess

|[智能语音导航的RAM鉴权]()|
|区块链服务|区块链服务|√|√|资源级别|-   AliyunBaaSFullAccess
-   AliyunBaaSReadOnlyAccess

|[Hyperledger Fabric RAM鉴权](/cn.zh-CN/API参考/Hyperledger Fabric RAM鉴权.md)|
|区块链服务|分布式数字身份|√|√|资源级别|-   AliyunBaasDisFullAccess
-   AliyunBaasDisReadOnlyAccess

|[分布式数字身份的RAM鉴权]()|
|区块链服务|可信计算服务|√|√|资源级别|-   AliyunBaasCccsFullAccess
-   AliyunBaasCccsReadOnlyAccess

|-|
|宜搭|-|√|○|服务级别|-|-|
|云价签|-|√|○|服务级别|-|[云价签的RAM鉴权](https://help.aliyun.com/document_detail/130700.html)|
|智能外呼机器人|-|√|√|操作级别|-   AliyunOutboundbotFullAccess
-   AliyunOutboundbotReadOnlyAccess

|-|
|云行情|-|√|○|服务级别|-   AliyunCQLoudFullAccess
-   AliyunCQLoudReadOnlyAccess

|-|
|智能双录质检|-|√|√|服务级别|-   AliyunIdrsServiceFullAccess
-   AliyunIdrsServiceReadOnly

|[智能双录质检的RAM鉴权]()|
|智能数据助理|-|√|○|服务级别|AliyunChatbotFullAccess|-|
|应用发现服务|-|√|○|服务级别|-   AliyunAPDSFullAccess
-   AliyunAPDSReadOnlyAccess

|-|
|微服务引擎|微服务引擎|√|√|资源级别|-   AliyunMSEFullAccess
-   AliyunMSEReadOnlyAccess

|[RAM用户使用MSE](/cn.zh-CN/微服务注册配置中心/权限管理/RAM授权访问注册配置中心.md)|
|微服务引擎|微服务网关|√|√|资源级别|-   AliyunMicrogatewayFullAccess
-   AliyunMicrogatewayReadOnlyAccess

|[微服务网关的RAM鉴权]()|
|Teambition|-|√|○|服务级别|-|-|
|金融分布式架构|-|√|○|服务级别|-   AliyunSOFAFullAccess
-   AliyunSOFAReadOnlyAccess

|-|
|客服工作台|-|×|○|-|-|-|
|智能设计|-|√|○|服务级别|AliyunLubanFullAccess|-|
|钉钉移动办公智能硬件套件|-|×|×|-|-|-|
|专属钉钉|-|×|○|-|-|-|
|政务钉钉|-|×|×|-|-|-|

## 移动云

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|移动用户反馈|-|√|○|服务级别|-   AliyunFeedbackFullAccess
-   AliyunFeedbackReadOnlyAccess

|[移动用户反馈的RAM鉴权](https://help.aliyun.com/document_detail/55906.html)|
|移动热修复|-|√|√|服务级别|-   AliyunHotfixFullAccess
-   AliyunHotfixReadOnlyAccess

|[移动热修复的RAM鉴权](https://help.aliyun.com/document_detail/55889.html)|
|移动推送|-|√|√|服务级别|-   AliyunMPushFullAccess
-   AliyunMPushReadOnlyAccess

|[移动推送的RAM鉴权](https://help.aliyun.com/document_detail/48059.html)|
|移动测试|-|√|○|资源级别|-   AliyunMobileTestingReadOnlyAccess
-   AliyunMobileTestingFullAccess

|[移动测试的RAM鉴权](https://help.aliyun.com/document_detail/93670.html)|
|移动数据分析|-|√|○|服务级别|-|[移动数据分析的RAM鉴权](https://help.aliyun.com/document_detail/56608.html)|
|移动研发平台|-|√|√|资源级别|-   AliyunEmasDevOpsFullAccess
-   AliyunEmasDevOpsReadOnlyAccess

|-|
|小程序云|-|√|√|操作级别|-   AliyunMPCAFullAccess
-   AliyunMPCAReadOnlyAccess

|-|

## 域名与网站

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|云解析DNS|云解析DNS|√|√|资源级别|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|[云解析DNS的RAM鉴权](/cn.zh-CN/API文档/RAM鉴权.md)|
|云解析DNS|IP地理位置库|√|√|资源级别|-   AliyunGeoipFullAccess
-   AliyunGeoipReadOnlyAccess

|[IP地理位置的RAM鉴权]()|
|云解析DNS|公共DNS|√|√|资源级别|-   AliyunPubDNSReadOnlyAccess
-   AliyunPubDNSFullAccess

|-|
|域名|-|√|√|资源级别|AliyunDomainFullAccess|[域名的RAM鉴权](/cn.zh-CN/域名管理/RAM资源授权-域名/Domain API鉴权规则.md)|
|云虚拟主机|-|×|×|-|-|-|
|弹性Web托管|-|×|×|-|-|-|
|商标服务|-|×|×|-|-|-|
|工商财税|-|√|○|服务级别|-   AliyunCompanyregFullAccess
-   AliyunCompanyregReadOnlyAccess

|-|
|HTTPDNS|-|√|√|资源级别|-   AliyunHTTPDNSFullAccess
-   AliyunHTTPDNSReadOnlyAccess

|-|
|版权与专利服务|-|×|×|-|-|-|
|图片与设计|-|√|√|服务级别|-   AliyunPremiumpicsFullAccess
-   AliyunPremiumpicsReadOnlyAccess
-   AliyunPremiumpicsDesignerAccess

|-|

## 人工智能

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|货架商品识别与管理|-|√|√|资源级别|-|-|
|三维空间重建|-|√|○|服务级别|-   AliyunTDSRFullAccess
-   AliyunTDSRreadOnlyAccess
-   AliyunTDSRDataCollectionAccess

|-|
|智能语义理解|-|√|√|资源级别|-   AliyunIQAFullAccess
-   AliyunIQAReadOnlyAccess

|-|
|卫星及无人机遥感影像分析产品|-|√|√|资源级别|-   AliyunRsimganalysFullAccess
-   AliyunRsimganalysReadOnlyAccess

|-|
|多媒体AI|多媒体AI|√|√|操作级别|-   AliyunMultimediaAIFullAccess
-   AliyunMultimediaAIReadOnlyAccess

|[多媒体AI的RAM鉴权](https://help.aliyun.com/document_detail/139940.html)|
|多媒体AI|短视频生产平台|√|○|服务级别|-   AliyunSVGPFullAccess
-   AliyunSVGPReadOnlyAccess

|-|
|视觉智能开放平台|-|√|√|操作级别|AliyunVIAPIFullAccess|-|
|地址标准化|-|√|√|服务级别|-|-|
|智能语音交互|-|√|√|服务级别|-   AliyunNLSFullAccess
-   AliyunNLSReadOnlyAccess

|-|
|机器学习|-|√|√|服务级别|-|-|
|自然语言处理|自然语言|√|√|服务级别|-|-|
|自然语言处理|智能短信|√|○|服务级别|-|-|
|人脸识别|-|√|√|服务级别|-|-|
|图像搜索|-|√|√|资源级别|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[图像搜索的RAM鉴权](https://help.aliyun.com/document_detail/179180.html)|
|机器翻译|-|√|√|服务级别|-|-|
|图像识别|-|√|√|服务级别|-|-|
|印刷文字识别|-|√|√|服务级别|-|-|
|城市视觉智能引擎|-|√|√|资源级别|-|-|
|交通云控平台|-|√|√|服务级别|-|-|
|视觉计算服务|-|√|√|服务级别|AliyunVCSFullAccess|-|
|智能视觉生产|-|√|√|操作级别|AliyunIVPDFullAccess|-|
|全息空间|-|√|○|操作级别|-|-|

## IoT物联网

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|物联网无线连接服务|-|√|√|服务级别|-   AliyunDyiotFullAccess
-   AliyunDyiotReadOnly

|[物联网无线连接服务的RAM鉴权](https://help.aliyun.com/document_detail/59434.html)|
|物联网平台|-|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[物联网平台的RAM鉴权](/cn.zh-CN/权限管理/账号授权/RAM授权管理/RAM用户访问.md)|
|物联网络管理平台|-|√|√|资源级别|-   AliyunLinkWANFullAccess
-   AliyunLinkWANReadOnlyAccess

|[物联网络管理平台的RAM鉴权](物联网络管理平台的RAM鉴权t1852002.dita#concept_2128847)|
|IoT设备身份认证|-|√|√|资源级别|-   AliyunIOTIDFullAccess
-   AliyunIOTIDReadOnlyAccess
-   AliyunIOTIDVerifyAccess

|-|
|物联网边缘计算|-|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[物联网边缘计算的RAM鉴权](/cn.zh-CN/物联网边缘计算（旧版本）/用户指南/云资源访问.md)|
|IoT安全运营中心|IoT安全运营中心|√|√|操作级别|-   AliyunISOCFullAccess
-   AliyunISOCReadOnlyAccess

|-|
|IoT安全运营中心|IoT固件安全检测FSS|√|√|资源级别|-   AliyunFSSFullAccess
-   AliyunFssReadOnlyAccess

|[FSS的RAM鉴权](https://help.aliyun.com/document_detail/150641.html?spm=a2c4g.11186623.6.559.398e776dBZ9JN4)|
|物联网数据分析|-|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|-|
|智联车管理云平台|-|√|√|服务级别|-   AliyunIoVCCFullAccess
-   AliyunIoVCCConfigAccess
-   AliyunIoVCCReadOnlyAccess

|-|
|物联网智能视频服务|-|√|√|操作级别|-   AliyunLinkVisualFullAccess
-   AliyunLinkVisualReadOnlyAccess

|-|
|云原生多模数据库Lindorm|云原生多模数据库Lindorm|√|√|资源级别|-   AliyunLindormFullAccess
-   AliyunLindormReadOnlyAccess

|-|
|云原生多模数据库Lindorm|时序数据库TSDB|√|√|操作级别|-   AliyunHiTSDBReadOnlyAccess
-   AliyunHiTSDBFullAccess

|-|

## 大数据

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|DataWorks|-|√|√|服务级别|AliyunDataWorksFullAccess|[DataWorks的RAM鉴权]()|
|Quick BI|-|√|√|服务级别|-|-|
|DataV数据可视化|-|√|○|服务级别|AliyunDataVFullAccess|-|
|实时计算Flink版|-|√|√|服务级别|-|-|
|数据集成|-|√|√|服务级别|-|-|
|Elasticsearch|-|√|√|资源级别|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[Elasticsearch的RAM鉴权](/cn.zh-CN/访问控制/授权资源类型.md)|
|关系网络分析|-|√|√|服务级别|AliyunIPlusFullAccess|-|
|智能用户增长|-|×|○|-|-|-|
|E-MapReduce|-|√|√|服务级别|-   AliyunEMRFullAccess
-   AliyunUEMReadOnlyAccess
-   AliyunEMRFlowAdmin
-   AliyunEMRDevelopAccess

|-|
|开放搜索|-|√|√|资源级别|-   AliyunOpenSearchFullAccess
-   AliyunOpenSearchReadOnlyAccess

|[开放搜索的RAM鉴权](https://help.aliyun.com/document_detail/181629.html)|
|日志服务|-|√|√|资源级别|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[日志服务的RAM鉴权](/cn.zh-CN/开发指南/API参考/鉴权规则/鉴权规则.md)|
|智能推荐|-|√|√|资源级别|-   AliyunAIRecFullAccess
-   AliyunAIRecReadOnlyAccess

|-|
|工业大脑开放平台|-|√|○|资源级别|-   AliyunBrainIndustrialFullAccess
-   AliyunBrainIndustrialReadOnlyAccess

|-   [步骤一：开通PlatSimu服务]()
-   [步骤一：开通CloudPID服务]() |
|企业图谱|-|√|√|服务级别|-|-|
|数据资源平台|-|√|√|服务级别|-|-|
|数据湖构建|-|√|√|资源级别|-   AliyunDLFFullAccess
-   AliyunDLFReadOnlyAccess
-   AliyunDLADeveloperAccess

|-|
|大数据计算服务|-|√|√|服务级别|-|-|
|图计算服务|-|√|√|服务级别|-|-|
|数据总线|-|√|√|资源级别|-   AliyunDataHubFullAccess
-   AliyunDataHubReadOnlyAccess
-   AliyunDataHubSubscribeAccess
-   AliyunDataHubPublishAccess

|[数据总线权限控制](https://help.aliyun.com/document_detail/158779.html)|
|Databricks数据洞察|-|√|√|资源级别|AliyunDDIFullAccess|[数据洞察的RAM鉴权]()|
|交互式分析|-|√|√|资源级别|-   AliyunHologresFullAccess
-   AliyunHologresReadOnlyAccess

|[RAM用户使用Hologres快速入门](/cn.zh-CN/快速入门/RAM用户使用Hologres快速入门.md)|
|智能数据构建与管理Dataphin|-|√|√|服务级别|-|-|

## 开发者服务

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|Dragonwell|-|×|○|服务级别|-|-|
|CodePipeline|-|√|√|资源级别|AliyunCodePipelineFullAccess|[CodePipeline的RAM鉴权](https://help.aliyun.com/document_detail/63799.html)|
|云效|-|√|√|资源级别|-   AliyunRDCFullAccess
-   AliyunRDCReadOnlyAccess

|-|
|Node.js性能平台|-|√|○|服务级别|AliyunNPPFullAccess|[Node.js性能平台的RAM鉴权](https://help.aliyun.com/document_detail/65672.html)|
|链路追踪|-|√|√|服务级别|-   AliyunTracingAnalysisFullAccess
-   AliyunTracingAnalysisReadOnlyAccess

|-|
|Prometheus监控|-|√|√|服务级别|-   AliyunARMSFullAccess
-   AliyunARMSReadOnlyAccess

|-|
|移动开发平台mPaaS|-|√|○|服务级别|-   AliyunMPAASFullAccess
-   AliyunMPAASReadOnlyAccess

|-|
|云架构设计工具|-|√|○|服务级别|-   AliyunCADTFullAccess
-   AliyunCADTReadOnlyAccess

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
|游戏盾|-|√|○|服务级别|-   AliyunYundunGameShieldReadOnlyAccess
-   AliyunYundunGameShieldFullAccess

|-|
|Web应用防火墙|Web应用防火墙|√|√|服务级别|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|Web应用防火墙|人机验证（数据风控）|√|√|服务级别|AliyunYundunAFSFullAccess|-|
|SSL证书|-|√|√|服务级别|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|风险识别|-|√|√|服务级别|-   AliyunYundunSAFFullAccess
-   AliyunYundunSAFReadOnlyAccess

|-|
|安全众测|-|√|○|服务级别|-   AliyunYundunXianzhiFullAccess
-   AliyunYundunXianzhiReadOnlyAccess

|-|
|云防火墙|-|√|√|服务级别|-   AliyunYundunCloudFirewallReadOnlyAccess
-   AliyunYundunCloudFirewallFullAccess

|-|
|实人认证|实人认证|√|√|服务级别|-   AliyunYundunCloudAuthReadOnlyAccess
-   AliyunYundunCloudAuthFullAccess

|-|
|实人认证|金融级实人认证|√|√|服务级别|-   AliyunAntCloudAuthFullAccess
-   AliyunAntCloudAuthReadOnlyAccess

|-|
|漏洞扫描|-|√|√|服务级别|AliyunYundunAvdsFullAccess|-|
|安全管家|-|√|○|服务级别|-|-|
|加密服务|-|√|○|服务级别|-   AliyunYundunHSMFullAccess
-   AliyunYundunHSMReadOnlyAccess

|-|
|内容安全|-|√|√|服务级别|AliyunYundunGreenWebFullAccess|-|
|数据库审计|-|√|√|服务级别|-   AliyunYundunDbAuditFullAccess
-   AliyunYundunDbAuditReadOnlyAccess

|-|
|堡垒机|堡垒机|√|○|服务级别|-   AliyunYundunBastionHostFullAccess
-   AliyunYundunBastionHostReadOnlyAccess
-   AliyunYundunBastionHostOperateOnlyAccess
-   AliyunYundunBastionHostAuditOnlyAccess

|-|
|堡垒机|特权访问服务|√|○|操作级别|-   AliyunBastionhostPamFullAccess
-   AliyunBastionhostPamReadOnlyAccess

|[堡垒机的RAM鉴权]()|
|爬虫风险管理|-|√|○|服务级别|-   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

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

|[使用RAM实现对资源的访问控制](/cn.zh-CN/访问控制与审计/使用RAM实现对资源的访问控制.md)|
|访问控制|-|√|√|资源级别|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/API参考（RAM）/RAM鉴权.md)|
|操作审计|-|√|√|操作级别|-   AliyunActionTrailFullAccess
-   AliyunActionTrailReadOnlyAccess
-   AliyunActionTrailDeliveryPolicy

|[操作审计的RAM鉴权](/cn.zh-CN/API参考/API参考（2017-12-04）（不推荐）/RAM鉴权.md)|
|终端访问控制系统|-|√|○|操作级别|-   AliyunUEMFullAccess
-   AliyunUEMReadOnlyAccess

|-|
|云安全访问服务|-|√|○|服务级别|-|-|

## 支持与服务

|云服务|子服务/子模块|控制台|API|授权粒度|系统策略|相关文档|
|:--|-------|:--|:--|:---|:---|:---|
|工单|-|√|√|服务级别|AliyunSupportFullAccess|-|
|智能在线|-|×|○|-|-|-|
|迁云咨询服务|-|×|×|-|-|-|
|应用架构咨询服务|-|×|×|-|-|-|
|大数据应用咨询服务|-|×|×|-|-|-|
|DevOps咨询服务|-|×|×|-|-|-|
|云化战略咨询服务|-|×|×|-|-|-|
|SAP®上云解决方案咨询服务|-|×|×|-|-|-|
|迁云实施服务|-|×|×|-|-|-|
|大数据应用实施服务|-|×|×|-|-|-|
|云原生交付服务|-|×|×|-|-|-|
|云上稳定性保障服务|-|×|×|-|-|-|
|云上护航服务（尊享版）驻场包|-|×|×|-|-|-|
|技术托管服务|-|×|×|-|-|-|
|GTS专家服务|-|×|×|-|-|-|
|运维服务|-|×|×|-|-|-|
|云上数据库优化服务|-|×|×|-|-|-|
|应用架构优化服务|-|×|×|-|-|-|

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

|[费用中心的RAM鉴权](https://help.aliyun.com/document_detail/88883.html)

[API调用授权](https://help.aliyun.com/document_detail/139650.html) |
|配额中心|-|√|√|资源级别|-   AliyunQuotasFullAccess
-   AliyunQuotasReadOnlyAccess

|[配额中心的RAM鉴权]()|
|分销平台|-|√|○|服务级别|-   AliyunAgencyFullAccess
-   AliyunAgencyEcoPickOrderFullAccess
-   AliyunAgencyCustomerOrderAssociatedProjectFullAccess
-   AliyunAgencyCustomerOrderAssociatedProjectReadOnlyAccess

|-|
|消息中心|-|√|○|服务级别|-   AliyunNotificationsFullAccess
-   AliyunNotificationsReadOnlyAccess

|-|
|备案|-|√|○|服务级别|AliyunBeianFullAccess|-|

