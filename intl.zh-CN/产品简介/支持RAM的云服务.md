# 支持RAM的云服务

本文罗列了与访问控制（RAM）相集成的阿里云服务，并提供每个服务支持的授权粒度、系统策略以及相关文档，方便您查询和使用。

## 支持RAM的云服务列表

以下表格分别罗列了阿里云各个模块下支持RAM的云服务：[弹性计算](#section_01)、[数据库](#section_02)、[存储与CDN](#section_03)、[网络](#section_04)、[分析](#section_05)、[云通信](#section_06)、[管理与监控](#section_07)、[应用服务](#section_08)、[物联网IOT](#section_lqo_m79_230)、[消息队列MQ](#section_nur_e8z_9qt)、[互联网中间件](#section_09)、[视频服务](#section_12)、[大数据（数加）](#section_13)、[安全（云盾）](#section_14)、[云市场](#section_15)、[域名与网站](#section_16)、[会员服务](#section_17)、[费用中心](#section_18)、[工单](#section_19)、[消息](#section_20)。

关于阿里云各个模块下支持STS的云服务，请参见[支持STS的云服务](/intl.zh-CN/产品简介/支持STS的云服务.md)。

每个表格包含以下信息：

-   服务名：支持RAM的云服务的名称。
-   控制台：当前服务是否支持在控制台进行访问控制，“√”表示支持，“×”表示不支持，“○”表示该服务未接入控制台。
-   API：当前服务是否支持通过API进行访问控制，“√”表示支持，“×”表示不支持，“○”表示该服务未提供API。
-   授权粒度：当前服务提供的最小授权粒度，“-”表示暂无。

    在与RAM集成时，各产品针对RAM用户定义了不同级别的授权粒度：

    -   服务级别：将云服务作为一个整体进行授权。一个RAM用户只能处于对这个产品拥有所有权限和没有任何权限两种状态。
    -   操作级别：API级别的授权。一个RAM用户可以对指定云服务的某类资源执行某几个指定的操作。
    -   资源级别：对执行资源的指定操作进行授权（最细的授权粒度）。例如：授权一个RAM用户仅可对某一台云服务器进行重启操作。
-   系统策略：当前云服务支持的系统策略，“-”表示暂无。
-   相关文档：当前服务与RAM相关的文档链接，“-”表示暂无。

## 弹性计算

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云服务器ECS|√|√|资源级别|-   AliyunECSFullAccess
-   AliyunECSReadOnlyAccess
-   AliyunECSNetworkInterfaceManagementAccess

|[鉴权规则](/intl.zh-CN/API参考/鉴权规则.md)|
|弹性伸缩Auto Scaling|√|√|服务级别|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[API使用须知](/intl.zh-CN/API参考/API使用须知.md)|
|容器服务Kubernetes版|√|√|资源级别|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[使用子账号](/intl.zh-CN/用户指南/授权管理/使用子账号.md)|
|容器镜像服务|√|√|资源级别|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[仓库访问控制](https://www.alibabacloud.com/help/zh/doc-detail/67992.htm)|
|资源编排ROS|√|√|服务级别|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[使用RAM控制资源访问](/intl.zh-CN/快速入门/使用RAM控制资源访问.md)|
|批量计算|√|√|服务级别|-

|-|
|函数计算|√|√|资源级别|-   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

|[子账号控制台快速指导](https://www.alibabacloud.com/help/zh/doc-detail/55617.html)|
|弹性高性能计算E-HPC|√|√|服务级别|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|轻量应用服务器|√|○|服务级别|AliyunSWASFullAccess|-|
|弹性容器实例ECI|√|√|资源级别|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[如何为子账号授权](https://www.alibabacloud.com/help/zh/doc-detail/92790.htm)|
|Web应用托管服务（Web+）|√|√|操作级别|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|- |
|运维编排服务|√|√|资源级别|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[鉴权规则](https://www.alibabacloud.com/help/zh/doc-detail/123024.htm)|

## 数据库

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云数据库PolarDB|√|√|操作级别|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[创建和使用子账号](/intl.zh-CN/用户指南/账号和数据库/创建和管理RAM用户.md)|
|云数据库RDS版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RAM资源授权](/intl.zh-CN/API 参考/RAM资源授权.md)|
|云数据库MongoDB版|√|√|资源级别|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|- |
|云数据库Redis版|√|√|资源级别|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|云数据库Memcache版|√|√|服务级别|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|云数据库HBase|√|√|资源级别|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[子账号管理集群](t1857011.md#)|
|时序数据库TSDB|√|√|操作级别|-

|-|
|云原生数据仓库ADB PostgreSQL版|√|√|资源级别|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[API的鉴权规则](/intl.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md)|
|云原生数据仓库ADB MySQL版|√|√|资源级别|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[t1854382.dita\#multiTask1017]()|
|数据传输服务DTS|√|√|操作级别|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

| |
|数据库备份DBS|√|√|服务级别|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|数据库自治服务DAS|√|√|服务级别|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[子账号如何使用DAS](https://www.alibabacloud.com/help/zh/doc-detail/66674.htm)|
|云原生分布式数据库 PolarDB-X（原DRDS升级版）|√|√|资源级别|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[DRDS支持的资源授权](https://www.alibabacloud.com/help/zh/doc-detail/51480.htm)|
|数据库和应用迁移服务ADAM|√|○|服务级别|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[RAM 子账号]()|
|数据库网关DG|√|√|资源级别|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|
|可信账本数据库|√|√|资源级别|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[子账号授权]()|

## 存储与CDN

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|对象存储OSS|√|√|资源级别|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[RAM Policy概述](/intl.zh-CN/开发指南/数据安全/访问控制/RAM Policy/基于RAM Policy的权限控制.md)|
|文件存储NAS|√|√|操作级别|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[管理权限组]()|
|表格存储Tablestore|√|√|资源级别|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[自定义权限](/intl.zh-CN/功能介绍/授权管理/自定义权限.md)|
|云存储网关|√|√|服务级别|AliyunHCSSGWFullAccess|-|
|混合云备份|√|○|资源级别|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|-|
|闪电立方|√|○|服务级别|AliyunMGWFullAccess|-|
|全站加速|√|√|资源级别|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|CDN|√|√|资源级别|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/新版API参考/RAM鉴权.md)|

## 网络

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|专有网络VPC|√|√|资源级别|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|负载均衡|√|√|资源级别|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[RAM鉴权](/intl.zh-CN/传统型负载均衡CLB/开发指南/API参考/RAM鉴权.md)|
|弹性公网IP|√|√|资源级别|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|高速通道|√|√|资源级别|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|NAT网关|√|√|资源级别|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|VPN网关|√|√|资源级别|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|共享带宽|√|√|资源级别|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|全球加速|√|√|资源级别|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|智能接入网关|√|√|资源级别|-

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|
|云企业网|√|√|资源级别|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[RAM鉴权]()|

## 分析

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|E-MapReduce|√|√|服务级别|-   AliyunEMRFullAccess
-   AliyunEMRDevelopAccess
-   AliyunEMRFlowAdmin

|-|
|数据湖分析|√|√|操作级别|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

|-|

## 云通信

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|短信服务|√|√|服务级别|-

|- |

## 管理与监控

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云监控|√|√|操作级别|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

|[访问控制](/intl.zh-CN/附录3 账号授权相关/访问控制.md)|
|操作审计|√|√|资源级别|-

|[RAM鉴权](/intl.zh-CN/API参考/API参考（2017-12-04）/RAM鉴权.md)|
|访问控制|√|√|资源级别|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/API参考（RAM）/RAM鉴权.md)|
|密钥管理服务|√|√|资源级别|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[使用RAM实现对资源的访问控制](/intl.zh-CN/访问控制与审计/使用RAM实现对资源的访问控制.md)|
|智能顾问|×|×|操作级别|-|-|
|资源管理|√|√|资源级别|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[RAM鉴权]()|
|配置审计|√|√|服务级别|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[RAM鉴权](/intl.zh-CN/API参考/RAM鉴权.md)|

## 应用服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|日志服务|√|√|资源级别|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[鉴权规则](/intl.zh-CN/开发指南/API 参考/RAM/STS/鉴权规则.md)|
|邮件推送|√|√|服务级别|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API网关|√|√|服务级别|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[使用 RAM 管理 API]()|
|区块链服务BaaS|√|√|资源级别|-|[Hyperledger Fabric RAM鉴权](/intl.zh-CN/API参考/Hyperledger Fabric RAM鉴权.md)|
|小程序云|√|√|操作级别|-   AliyunMPCAFullAccess
-   AliyunMPCAReadOnlyAccess

|-|

## 物联网IOT

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|物联网平台|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[RAM用户访问](/intl.zh-CN/账号与登录/账号授权/RAM授权管理/RAM用户访问.md)|
|物联网边缘计算|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[云资源访问](/intl.zh-CN/用户指南/云资源访问.md)|

## 消息队列MQ

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息队列for Apache Rocket MQ|√|√|资源级别|-   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[RAM主子账号授权](https://www.alibabacloud.com/help/zh/doc-detail/61382.htm)|
|消息服务MNS|√|√|资源级别|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|- |

## 互联网中间件

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|企业级分布式应用服务EDAS|√|√|服务级别|AliyunEDASFullAccess|[子账号管理](https://www.alibabacloud.com/help/zh/doc-detail/44023.htm)|
|应用实时监控服务ARMS|√|√|服务级别|AliyunARMSFullAccess|[借助RAM用户实现分权](/intl.zh-CN/访问控制/借助RAM用户实现分权.md)|
|应用配置管理|√|√|资源级别|AliyunACMFullAccess|[访问权限控制](/intl.zh-CN/访问控制/访问权限控制.md)|
|全局事务服务|√|√|服务级别|-   AliyunGTSFullAccess
-   AliyunGTSReadOnlyAccess

|-|

## 视频服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|媒体处理|√|√|服务级别|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|[子帐号使用控制台说明](/intl.zh-CN/用户指南/子帐号使用控制台说明.md)|
|视频点播|√|√|服务级别|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|视频直播|√|√|资源级别|AliyunLiveFullAccess|[API鉴权规则](/intl.zh-CN/API参考/API鉴权规则.md)|
|音视频通信RTC|√|√|资源级别|-

|- |
|云视频会议|√|○|资源级别|-   AliyunCVCFullAccess
-   AliyunCVCReadOnlyAccess

|-|

## 大数据（数加）

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|DataWorks|√|√|服务级别|AliyunDataWorksFullAccess|[用户使用子账号]()|
|Quick BI|√|√|服务级别|-|-|
|机器学习PAI|√|√|服务级别|-|-|
|公众趋势分析|√|√|服务级别|-|-|
|DataV数据可视化|√|√|服务级别|-|-|
|MaxCompute|√|√|服务级别|-|-|
|阿里云Elasticsearch|√|√|资源级别|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[授权资源类型](/intl.zh-CN/访问控制/授权资源类型.md)|
|机器翻译|×|×|服务级别|-|-|
|图像搜索|√|√|资源级别|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[授权访问鉴权规则](https://www.alibabacloud.com/help/zh/doc-detail/179180.htm)|

## 安全（云盾）

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云安全中心（态势感知）|√|√|服务级别|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|云安全中心（安骑士）|√|√|服务级别|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|DDoS基础防护|√|√|服务级别|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|DDoS高防|√|√|服务级别|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|DDoS高防（国际）|√|○|服务级别|-   AliyunYundunAntiDDoSPremiumFullAccess
-   AliyunYundunAntiDDoSPremiumReadOnlyAccess

|-|
|游戏盾|√|○|服务级别|AliyunYundunGameShieldReadOnlyAccess

|-|
|Web应用防火墙（网络安全）|√|√|服务级别|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL证书（应用安全）|√|√|服务级别|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|漏洞扫描（应用安全）|√|√|服务级别|AliyunYundunAvdsFullAccess|-|
|内容安全（业务安全）|√|√|服务级别|AliyunYundunGreenWebFullAccess|-|
|爬虫风险管理|√|○|服务级别|-   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

|-|
|金融级实人认证|√|√|服务级别|-   AliyunAntCloudAuthFullAccess
-   AliyunAntCloudAuthReadOnlyAccess

|-|

## 云市场

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云市场|√|○|服务级别|AliyunMarketplaceFullAccess|-|

## 域名与网站

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云解析DNS|√|√|资源级别|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|-|
|域名|√|√|资源级别|AliyunDomainFullAccess|[Domain API鉴权规则](/intl.zh-CN/域名管理/RAM资源授权-域名/Domain API鉴权规则.md)|
|云虚拟主机|×|×|-|-|-|
|企业邮箱|×|×|-|-|-|

## 会员服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|备案|√|○|服务级别|AliyunBeianFullAccess|-|

## 费用中心

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|费用中心|√|√|服务级别|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|- |

## 工单

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|工单|√|√|服务级别|AliyunSupportFullAccess|-|

## 消息

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息中心|√|○|服务级别|AliyunNotificationsFullAccess|-|

