# 支持RAM的云服务

本文罗列了与访问控制（RAM）相集成的阿里云服务，并提供每个服务支持的授权粒度、系统策略以及相关文档，方便您查询和使用。

## 支持RAM的云服务列表

以下表格分别罗列了阿里云各个模块下支持RAM的云服务：[弹性计算](#section_01)、[数据库](#section_02)、[存储与CDN](#section_03)、[网络](#section_04)、[分析](#section_05)、[云通信](#section_06)、[人工智能](#section_fho_ls1_75c)、[数字金融](#section_2fs_dhk_v2h)、[管理与监控](#section_07)、[应用服务](#section_08)、[物联网IOT](#section_lqo_m79_230)、[消息队列MQ](#section_nur_e8z_9qt)、[互联网中间件](#section_09)、[移动研发平台EMAS](#section_11)、[视频服务](#section_12)、[大数据（数加）](#section_13)、[安全（云盾）](#section_14)、[云市场](#section_15)、[域名与网站](#section_16)、[会员服务](#section_17)、[费用中心](#section_18)、[工单](#section_19)、[消息](#section_20)、[企业控制台](#section_21)。

关于阿里云各个模块下支持STS的云服务，请参见[支持STS的云服务](/cn.zh-CN/产品简介/支持STS的云服务.md)。

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

|[鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|弹性伸缩Auto Scaling|√|√|服务级别|-   AliyunESSFullAccess
-   AliyunESSReadOnlyAccess

|[API使用须知](/cn.zh-CN/API参考/API使用须知.md)|
|容器服务Kubernetes版|√|√|资源级别|-   AliyunCSFullAccess
-   AliyunCSReadOnlyAccess

|[使用子账号](/cn.zh-CN/用户指南/授权管理/使用子账号.md)|
|容器镜像服务|√|√|资源级别|-   AliyunContainerRegistryFullAccess
-   AliyunContainerRegistryReadOnlyAccess

|[仓库访问控制](https://help.aliyun.com/document_detail/67992.html)|
|资源编排ROS|√|√|服务级别|-   AliyunROSFullAccess
-   AliyunROSReadOnlyAccess

|[使用RAM控制资源访问](/cn.zh-CN/快速入门/使用RAM控制资源访问.md)|
|批量计算|√|√|服务级别|AliyunBatchComputeFullAccess

|-|
|函数计算|√|√|资源级别|-   AliyunFCFullAccess
-   AliyunFCInvocationAccess
-   AliyunFCReadOnlyAccess

|[子账号控制台快速指导](https://help.aliyun.com/document_detail/55617.html)|
|弹性高性能计算E-HPC|√|√|服务级别|-   AliyunEHPCFullAccess
-   AliyunEHPCReadOnlyAccess

|-|
|轻量应用服务器|√|○|服务级别|AliyunSWASFullAccess|-|
|弹性容器实例ECI|√|√|资源级别|-   AliyunECIFullAccess
-   AliyunECIReadOnlyAccess

|[如何为子账号授权](https://help.aliyun.com/document_detail/92790.html)|
|Web应用托管服务（Web+）|√|√|操作级别|-   AliyunWebPlusFullAccess
-   AliyunWebPlusReadOnlyAccess

|[借助RAM用户实现分权](/cn.zh-CN/访问控制/借助 RAM 用户实现分权.md)|
|Serverless应用引擎（SAE）|√|√|服务级别|-   AliyunSAEFullAccess
-   AliyunSAEReadOnlyAccess

|-|
|Serverless工作流|√|√|资源级别|-   AliyunFnFFullAccess
-   AliyunFnFReadOnlyAccess

|[鉴权规则](/cn.zh-CN/API参考/鉴权规则.md)|
|运维编排服务|√|√|资源级别|-   AliyunOOSFullAccess
-   AliyunOOSReadOnlyAccess

|[鉴权规则](https://help.aliyun.com/document_detail/156144.html)|
|服务网格ASM|√|√|资源级别|-|[授权概述](https://help.aliyun.com/document_detail/169466.html)|

## 数据库

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云数据库PolarDB|√|√|操作级别|-   AliyunPolardbReadOnlyAccess
-   AliyunPolardbFullAccess

|[创建和使用子账号](/cn.zh-CN/用户指南/账号和数据库/创建和使用子账号.md)|
|云数据库RDS版|√|√|资源级别|-   AliyunRDSFullAccess
-   AliyunRDSReadOnlyAccess

|[RAM资源授权](/cn.zh-CN/API 参考/RAM资源授权.md)|
|云数据库MongoDB版|√|√|资源级别|-   AliyunMongoDBFullAccess
-   AliyunMongoDBReadOnlyAccess

|[MongoDB API的鉴权规则](/cn.zh-CN/API参考/如何使用RAM授权/MongoDB API的鉴权规则.md)|
|云数据库Redis版|√|√|资源级别|-   AliyunKvstoreFullAccess
-   AliyunKvstoreReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|云数据库Memcache版|√|√|服务级别|-   AliyunOCSFullAccess
-   AliyunOCSReadOnlyAccess

|-|
|云数据库HybridDB for MySQL|√|√|资源级别|-   AliyunPetaDataFullAccess
-   AliyunPetaDataReadOnlyAccess

|[API鉴权规则](/cn.zh-CN/API参考/如何使用RAM授权/API鉴权规则.md)|
|云数据库HBase|√|√|资源级别|-   AliyunHBaseFullAccess
-   AliyunHBaseReadOnlyAccess

|[子账号管理集群]()|
|时序时空数据库TSDB|√|√|操作级别|-   AliyunHiTSDBReadOnlyAccess
-   AliyunHiTSDBFullAccess

|-|
|云原生数据仓库ADB PostgreSQL版|√|√|资源级别|-   AliyunGPDBFullAccess
-   AliyunGPDBReadOnlyAccess

|[API的鉴权规则](/cn.zh-CN/API参考/如何使用RAM授权/API的鉴权规则.md)|
|云数据库OceanBase|√|○|服务级别|-   AliyunOceanBaseFullAccess
-   AliyunOceanBaseReadOnlyAccess

|-|
|云原生数据仓库ADB MySQL版|√|√|资源级别|-   AliyunADBFullAccess
-   AliyunADBReadOnlyAccess

|[t1854382.dita\#multiTask1017]()|
|数据传输服务DTS|√|√|操作级别|-   AliyunDTSFullAccess
-   AliyunDTSReadOnlyAccess

|[通过系统策略授权子账号管理DTS](/cn.zh-CN/访问控制/通过系统策略授权子账号管理DTS.md)|
|数据管理DMS|√|○|资源级别|-|[云资源授权](https://help.aliyun.com/document_detail/47571.html)|
|数据库备份DBS|√|√|服务级别|-   AliyunDBSFullAccess
-   AliyunDBSReadOnlyAccess

|-|
|数据库自治服务DAS|√|○|服务级别|-   AliyunHDMReadOnlyAccess
-   AliyunHDMFullAccess

|[子账号如何使用DAS](https://help.aliyun.com/knowledge_detail/66674.html)|
|云原生分布式数据库 PolarDB-X（原DRDS升级版）|√|√|资源级别|-   AliyunDRDSReadOnlyAccess
-   AliyunDRDSFullAccess

|[PolarDB-X支持的资源授权](https://help.aliyun.com/document_detail/51480.html)|
|图数据库GDB|√|√|资源级别|-   AliyunGDBFullAccess
-   AliyunGDBReadOnlyAccess

|-|
|数据库和应用迁移服务ADAM|√|○|服务级别|-   AliyunADAMReadOnlyAccess
-   AliyunADAMFullAccess

|[RAM 子账号]()|
|数据库专家服务|√|○|服务级别|AliyunDBESFullAccess|-|
|数据库网关DG|√|√|资源级别|-   AliyunDGFullAccess
-   AliyunDGReadOnlyAccess

|-|
|云数据库Cassandra版|√|√|资源级别|-   AliyunCassandraFullAccess
-   AliyunCassandraReadOnlyAccess

|[RAM子账号管理]()|
|云数据库ClickHouse|√|√|资源级别|-   AliyunClickHouseFullAccess
-   AliyunClickHouseReadOnlyAccess

|[RAM资源授权]()|
|可信账本数据库|√|√|资源级别|-   AliyunLedgerDBFullAccess
-   AliyunLedgerDBReadOnlyAccess

|[子账号授权]()|

## 存储与CDN

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|对象存储OSS|√|√|资源级别|-   AliyunOSSFullAccess
-   AliyunOSSReadOnlyAccess

|[基于RAM Policy的权限控制](/cn.zh-CN/开发指南/数据安全/访问控制/RAM Policy/基于RAM Policy的权限控制.md)|
|文件存储NAS|√|○|操作级别|-   AliyunNASFullAccess
-   AliyunNASReadOnlyAccess

|[管理权限组]()|
|表格存储Tablestore|√|√|资源级别|-   AliyunOTSFullAccess
-   AliyunOTSReadOnlyAccess
-   AliyunOTSWriteOnlyAccess

|[自定义权限](/cn.zh-CN/功能介绍/授权管理/自定义权限.md)|
|云存储网关|√|○|服务级别|AliyunHCSSGWFullAccess|-|
|智能云相册|√|√|资源级别|-   AliyunCloudPhotoFullAccess
-   AliyunCloudPhotoReadOnlyAccess

|[授权映射表](https://help.aliyun.com/document_detail/56485.html)|
|混合云备份|√|○|资源级别|-   AliyunHBRFullAccess
-   AliyunHBRReadOnlyAccess

|-|
|混合云容灾|√|○|服务级别|AliyunHDRFullAccess|-|
|智能媒体管理|√|√|服务级别|-   AliyunIMMReadOnlyAccess
-   AliyunIMMFullAccess

|[子账户使用指南](https://help.aliyun.com/document_detail/73265.html)|
|闪电立方|√|○|服务级别|AliyunMGWFullAccess|-|
|文件存储HDFS|√|√|资源级别|-|[使用RAM授权访问](/cn.zh-CN/用户指南/使用RAM授权访问.md)|
|内容协作平台|√|√|服务级别|-   AliyunCCPReadOnlyAccess
-   AliyunCCPFullAccess

|-|
|边缘节点服务ENS|√|√|资源级别|-   AliyunENSReadOnlyAccess
-   AliyunENSFullAccess

|-|
|安全加速SCDN|√|√|资源级别|-   AliyunSCDNReadOnlyAccess
-   AliyunSCDNFullAccess

|-|
|全站加速|√|√|资源级别|-   AliyunDCDNFullAccess
-   AliyunDCDNReadOnlyAccess

|-|
|PCDN|√|√|资源级别|-   AliyunPCDNFullAccess
-   AliyunPCDNReadOnlyAccess

|[PCDN API鉴权规则](https://help.aliyun.com/document_detail/58028.html)|
|CDN|√|√|资源级别|-   AliyunCDNFullAccess
-   AliyunCDNReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/新版API参考/RAM鉴权.md)|

## 网络

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|专有网络VPC|√|√|资源级别|-   AliyunVPCFullAccess
-   AliyunVPCReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|负载均衡|√|√|资源级别|-   AliyunSLBReadOnlyAccess
-   AliyunSLBFullAccess

|[RAM鉴权](/cn.zh-CN/开发指南/API参考/RAM鉴权.md)|
|共享流量包|√|○|服务级别|-|-|
|弹性公网IP|√|√|资源级别|-   AliyunEIPFullAccess
-   AliyunEIPReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|高速通道|√|√|资源级别|-   AliyunExpressConnectFullAccess
-   AliyunExpressConnectReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|NAT网关|√|√|资源级别|-   AliyunNATGatewayReadOnlyAccess
-   AliyunNATGatewayFullAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|VPN网关|√|√|资源级别|-   AliyunVPNGatewayFullAccess
-   AliyunVPNGatewayReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|共享带宽|√|√|资源级别|-   AliyunCommonBandwidthPackageReadOnlyAccess
-   AliyunCommonBandwidthPackageFullAccess

|-|
|全球加速|√|√|资源级别|-   AliyunGlobalAccelerationReadOnlyAccess
-   AliyunGlobalAccelerationFullAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|智能接入网关|√|√|资源级别|-   AliyunSmartAccessGatewayFullAccess
-   AliyunSmartAccessGatewayReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|IPv6转换服务|√|√|资源级别|-   AliyunIPv6TranslationFullAccess
-   AliyunIPv6TranslationReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|云企业网|√|√|资源级别|-   AliyunCENReadOnlyAccess
-   AliyunCENFullAccess

|[RAM鉴权]()|

## 分析

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|E-MapReduce|√|√|服务级别|AliyunEMRFullAccess

|-|
|数据湖分析|√|√|操作级别|-   AliyunDLAFullAccess
-   AliyunDLAReadOnlyAccess

|-|

## 云通信

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|语音服务|√|√|服务级别|-   AliyunDyvmsFullAccess
-   AliyunDyvmsReadOnlyAccess

|[语音权限访问控制](https://help.aliyun.com/document_detail/55766.html)|
|流量服务|√|√|服务级别|-   AliyunDycdpFullAccess
-   AliyunDycdpReadOnlyAccess

|-|
|短信服务|√|√|服务级别|-   AliyunDysmsFullAccess
-   AliyunDysmsReadOnlyAccess

|[访问权限控制](https://help.aliyun.com/document_detail/108069.html)|
|号码隐私保护|√|√|服务级别|-   AliyunDyplsFullAccess
-   AliyunDyplsReadOnlyAccess
-   AliyunCloudCommunicationFullAccess
-   AliyunCloudCommunicationReadOnlyAccess

|[号码权限访问控制](https://help.aliyun.com/document_detail/59872.html)|
|号码认证服务|√|√|服务级别|-   AliyunDypnsFullAccess
-   AliyunDypnsReadOnlyAccess

|[关于访问控制RAM](https://help.aliyun.com/document_detail/88440.html)|
|云通信网络加速|√|√|操作级别|-   AliyunSNSUFullAccess
-   AliyunSNSUReadOnlyAccess

|-|
|智能联络中心|√|○|资源级别|-|-|
|号码百科|√|√|操作级别|-   AliyunDytnsFullAccess
-   AliyunDytnsReadOnlyAccess

|[访问权限控制](https://help.aliyun.com/document_detail/154006.html?spm=a2c4g.11186623.6.551.4f505a58fSwtZC)|

## 人工智能

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|货架商品识别与管理|√|√|资源级别|-|-|
|三维空间重建|√|○|服务级别|AliyunTDSRFullAccess|-|
|智能语义理解|√|√|资源级别|-   AliyunIQAFullAccess
-   AliyunIQAReadOnlyAccess

|-|
|卫星及无人机遥感影像分析产品|√|√|资源级别|-   AliyunRsimganalysFullAccess
-   AliyunRsimganalysReadOnlyAccess

|-|
|多媒体AI|√|√|操作级别|-   AliyunMultimediaAIFullAccess
-   AliyunMultimediaAIReadOnlyAccess

|[鉴权认证](https://help.aliyun.com/document_detail/139940.html)|
|工业视觉智能|√|○|服务级别|-|-|
|阿里云视觉智能开放平台|√|√|服务级别|-|-|
|地址标准化|√|√|服务级别|-|-|

## 数字金融

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|移动开发平台mPaaS|√|○|服务级别|-   AliyunMPAASFullAccess
-   AliyunMPAASReadOnlyAccess

|-|
|金融分布式架构SOFAStack|√|○|服务级别|AliyunSOFAFullAccess|-|

## 管理与监控

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云监控|√|√|操作级别|-   AliyunCloudMonitorFullAccess
-   AliyunCloudMonitorReadOnlyAccess

|[访问控制](/cn.zh-CN/附录3 账号授权相关/访问控制.md)|
|操作审计|√|√|资源级别|-   AliyunActionTrailFullAccess
-   AliyunActionTrailReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|
|访问控制|√|√|资源级别|-   AliyunRAMFullAccess
-   AliyunRAMReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考（RAM）/RAM鉴权.md)|
|密钥管理服务|√|√|资源级别|-   AliyunKMSFullAccess
-   AliyunKMSReadOnlyAccess
-   AliyunKMSCryptoAccess

|[使用RAM实现对资源的访问控制](/cn.zh-CN/用户指南/使用RAM实现对资源的访问控制.md)|
|智能顾问|√|√|操作级别|-   AliyunAdvisorFullAccess
-   AliyunAdvisorReadOnlyAccess

|-|
|资源管理|√|○|资源级别|-   AliyunResourceDirectoryFullAccess
-   AliyunResourceDirectoryReadOnlyAccess

|[RAM鉴权]()|
|配置审计|√|○|服务级别|-   AliyunConfigFullAccess
-   AliyunConfigReadOnlyAccess

|[RAM鉴权](/cn.zh-CN/API参考/RAM鉴权.md)|

## 应用服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|日志服务|√|√|资源级别|-   AliyunLogFullAccess
-   AliyunLogReadOnlyAccess

|[鉴权规则](/cn.zh-CN/开发指南/API 参考/鉴权规则/鉴权规则.md)|
|开放搜索|√|√|资源级别|AliyunOpenSearchFullAccess|[访问鉴权规则](https://help.aliyun.com/document_detail/53744.html)|
|性能测试PTS|√|√|服务级别|AliyunPTSFullAccess|-|
|邮件推送|√|√|服务级别|-   AliyunDirectMailFullAccess
-   AliyunDirectMailReadOnlyAccess

|-|
|API网关|√|√|服务级别|-   AliyunApiGatewayFullAccess
-   AliyunApiGatewayReadOnlyAccess

|[使用 RAM 管理 API]()|
|智能对话分析|√|√|资源级别|-   AliyunSCAFullAccess
-   AliyunSCAReadOnlyAccess

|-|
|云效|√|√|资源级别|-   AliyunRDCFullAccess
-   AliyunRDCReadOnlyAccess

|-|
|云AP|×|×|-|-|-|
|云桌面|√|○|服务级别|AliyunGwsFullAccess|-|
|CodePipeline|√|√|资源级别|AliyunCodePipelineFullAccess|[授权策略示例](https://help.aliyun.com/document_detail/63799.html)|
|云客服|×|○|-|-|-|
|云小蜜|√|√|服务级别|AliyunChatbotFullAccess|-|
|云呼叫中心|√|√|服务级别|AliyunCCCFullAccess|-|
|Node.js性能平台|√|○|服务级别|AliyunNPPFullAccess|[子账号授权](https://help.aliyun.com/document_detail/65672.html)|
|API控制台|×|○|-|-|-|
|智联车管理云平台|√|√|服务级别|-   AliyunIoVCCFullAccess
-   AliyunIoVCCConfigAccess
-   AliyunIoVCCReadOnlyAccess

|-|
|区块链服务BaaS|√|√|资源级别|-|[Hyperledger Fabric RAM鉴权](/cn.zh-CN/API参考/Hyperledger Fabric RAM鉴权.md)|
|智能推荐|√|√|资源级别|-   AliyunAIRecFullAccess
-   AliyunAIRecReadOnlyAccess

|-|
|宜搭|√|○|服务级别|-|-|
|云价签|√|○|服务级别|-|[权限管理](https://help.aliyun.com/document_detail/130700.html)|
|IoT固件安全检测FSS|√|√|资源级别|-   AliyunFSSFullAccess
-   AliyunFssReadOnlyAccess

|[RAM鉴权](https://help.aliyun.com/document_detail/150641.html?spm=a2c4g.11186623.6.559.398e776dBZ9JN4)|
|智能外呼|√|√|操作级别|-   AliyunOutboundbotFullAccess
-   AliyunOutboundbotReadOnlyAccess

|-|
|智能语音导航|√|√|操作级别|-   AliyunVoiceNavigatorFullAccess
-   AliyunVoiceNavigatorReadOnlyAccess

|[RAM鉴权]()|
|云行情|√|○|服务级别|-   AliyunCQLoudFullAccess
-   AliyunCQLoudReadOnlyAccess

|-|
|逻辑编排|√|√|资源级别|-   AliyunLogicComposerFullAccess
-   AliyunLogicComposerReadOnlyAccess

|[自定义授权策略](https://help.aliyun.com/document_detail/127020.html)|
|小程序云|√|√|操作级别|-   AliyunMPCAFullAccess
-   AliyunMPCAReadOnlyAccess

|-|

## 物联网IOT

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|物联网无线连接服务|√|√|服务级别|-   AliyunDyiotFullAccess
-   AliyunDyiotReadOnly

|[访问权限控制](https://help.aliyun.com/document_detail/59434.html)|
|物联网平台|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[子账号访问](/cn.zh-CN/权限管理/账号授权/RAM授权管理/子账号访问.md)|
|物联网络管理平台|√|√|资源级别|-   AliyunLinkWANFullAccess
-   AliyunLinkWANReadOnlyAccess

|[t1852002.dita\#concept\_2128847](/cn.zh-CN/用户指南/RAM授权管理/子账号访问.md)|
|IoT设备身份认证|√|√|资源级别|-   AliyunIOTIDFullAccess
-   AliyunIOTIDReadOnlyAccess
-   AliyunIOTIDVerifyAccess

|-|
|物联网边缘计算|√|√|资源级别|-   AliyunIOTFullAccess
-   AliyunIOTReadOnlyAccess

|[云资源访问](/cn.zh-CN/用户指南/云资源访问.md)|

## 消息队列MQ

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息队列for Apache Rocket MQ|√|√|资源级别|-   AliyunMQFullAccess
-   AliyunMQPubOnlyAccess
-   AliyunMQSubOnlyAccess

|[RAM主子账号授权](https://help.aliyun.com/document_detail/61382.html)|
|消息队列Kafka版|√|√|服务级别|-   AliyunKafkaFullAccess
-   AliyunKafkaPubOnlyAccess
-   AliyunKafkaSubOnlyAccess

|[RAM用户授权（作废）]()|
|消息队列AMQP版|√|√|资源级别|-   AliyunAMQPFullAccess
-   AliyunAMQPReadOnlyAccess

|-|
|微消息队列for MQTT|√|√|服务级别|-|-|
|事件总线EventBridge|√|√|资源级别|-   AliyunEventBridgeFullAccess
-   AliyunEventBridgeReadOnlyAccess
-   AliyunEventBridgeResourceCreatePolicy
-   AliyunEventBridgeResourceDeletePolicy
-   AliyunEventBridgeResourceUpdatePolicy
-   AliyunEventBridgePutEventsPolicy

|[权限策略]()|
|消息服务MNS|√|√|资源级别|-   AliyunMNSFullAccess
-   AliyunMNSReadOnlyAccess

|[授权子账号访问MNS](https://help.aliyun.com/document_detail/27446.html)|

## 互联网中间件

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|企业级分布式应用服务EDAS|√|√|服务级别|AliyunEDASFullAccess|[子账号管理](https://help.aliyun.com/document_detail/44023.html)|
|应用实时监控服务ARMS|√|√|服务级别|AliyunARMSFullAccess|[借助RAM用户实现分权](/cn.zh-CN/访问控制/借助RAM用户实现分权.md)|
|云服务总线|√|√|资源级别|AliyunCSBFullAccess|[如何为RAM用户授权使用CSB]()|
|应用配置管理|√|√|资源级别|AliyunACMFullAccess|[访问权限控制](/cn.zh-CN/访问控制/访问权限控制.md)|
|链路追踪|√|○|服务级别|AliyunTracingAnalysisFullAccess|-|
|应用高可用服务|√|○|服务级别|-   AliyunAHASFullAccess
-   AliyunAHASReadOnlyAccess

|-|
|全局事务服务|√|○|服务级别|-   AliyunGTSFullAccess
-   AliyunGTSReadOnlyAccess

|-|
|微服务引擎MSE|√|○|服务级别|-   AliyunMSEFullAccess
-   AliyunMSEReadOnlyAccess

|[RAM用户使用MSE](/cn.zh-CN/用户指南/微服务组件托管/RAM用户使用MSE.md)|

## 移动研发平台EMAS

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|移动用户反馈|√|√|服务级别|-   AliyunFeedbackFullAccess
-   AliyunFeedbackReadOnlyAccess

|[鉴权Action与鉴权规则](https://help.aliyun.com/document_detail/55906.html)|
|移动热修复|√|√|服务级别|-   AliyunHotfixFullAccess
-   AliyunHotfixReadOnlyAccess

|[鉴权规则](https://help.aliyun.com/document_detail/55889.html)|
|移动推送|√|√|服务级别|-   AliyunMPushFullAccess
-   AliyunMPushReadOnlyAccess

|[鉴权规则](https://help.aliyun.com/document_detail/48059.html)|
|移动测试|√|○|资源级别|-   AliyunMobileTestingReadOnlyAccess
-   AliyunMobileTestingFullAccess

|[授权管理](https://help.aliyun.com/document_detail/93670.html)|
|移动数据分析|√|○|服务级别|-|[RAM子账号访问](https://help.aliyun.com/document_detail/56608.html)|
|移动DevOps|√|√|资源级别|-|-|
|HTTPDNS|√|√|资源级别|-|-|

## 视频服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|媒体处理|√|√|服务级别|-   AliyunMTSFullAccess
-   AliyunMTSPlayerAuth

|[子帐号使用控制台说明](/cn.zh-CN/用户指南/子帐号使用控制台说明.md)|
|视频点播|√|√|服务级别|-   AliyunVODFullAccess
-   AliyunVODReadOnlyAccess
-   AliyunVODPlayAuth
-   AliyunVODUploadAuth

|-|
|视频直播|√|√|资源级别|AliyunLiveFullAccess|[API鉴权规则](/cn.zh-CN/API参考/API鉴权规则.md)|
|音视频通信RTC|√|√|资源级别|-   AliyunRTCFullAccess
-   AliyunRTCReadOnlyAccess

|[RAM资源授权](https://help.aliyun.com/document_detail/74559.html)|
|智能视觉|√|√|服务级别|-   AliyunIVisionFullAccess
-   AliyunIVisionReadOnlyAccess

|-|
|视频监控|√|√|操作级别|AliyunVSFullAccess|-|
|视觉计算服务|√|○|服务级别|AliyunVCSFullAccess|-|
|云视频会议|√|○|资源级别|-   AliyunCVCFullAccess
-   AliyunCVCReadOnlyAccess

|-|

## 大数据（数加）

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|DataWorks|√|√|服务级别|AliyunDataWorksFullAccess|[用户使用子账号]()|
|Quick BI|√|√|服务级别|-|-|
|机器学习PAI|√|√|服务级别|-|-|
|推荐引擎|√|√|服务级别|-|-|
|公众趋势分析|√|√|服务级别|-|-|
|DataV数据可视化|√|√|服务级别|-|-|
|MaxCompute|√|√|服务级别|-|-|
|智能语音交互|√|√|服务级别|-   AliyunNLSFullAccess
-   AliyunNLSReadOnlyAccess

|-|
|实时计算|√|√|服务级别|-|-|
|画像分析|√|√|服务级别|-|-|
|企业图谱|√|√|服务级别|-|-|
|数据集成|√|√|服务级别|-|-|
|人脸识别|√|√|服务级别|-|-|
|图像识别|√|×|服务级别|-|-|
|阿里云Elasticsearch|√|√|资源级别|-   AliyunElasticsearchReadOnlyAccess
-   AliyunElasticsearchFullAccess

|[授权资源类型](/cn.zh-CN/ES访问控制/授权资源类型.md)|
|自然语言处理|×|√|服务级别|-|-|
|机器翻译|√|√|服务级别|-|-|
|智能数据构建与管理Dataphin|√|√|服务级别|-|-|
|I+关系网络分析|√|√|服务级别|-|-|
|图片与设计|√|√|服务级别|-   AliyunPremiumpicsFullAccess
-   AliyunPremiumpicsReadOnlyAccess
-   AliyunPremiumpicsDesignerAccess

|-|
|图像搜索|√|√|资源级别|-   AliyunImagesearchReadOnlyAccess
-   AliyunImagesearchFullAccess

|[RAM授权](https://help.aliyun.com/document_detail/179180.html)|
|图片优选服务|√|○|操作级别|-|-|
|智能用户增长|×|○|-|-|-|

## 安全（云盾）

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云安全中心（态势感知）|√|○|服务级别|-   AliyunYundunSASFullAccess
-   AliyunYundunSASReadOnlyAccess

|-|
|云安全中心（安骑士）|√|○|服务级别|-   AliyunYundunAegisFullAccess
-   AliyunYundunAegisReadOnlyAccess

|-|
|DDoS基础防护|√|○|服务级别|-   AliyunYundunDDosFullAccess
-   AliyunYundunDDosReadOnlyAccess

|-|
|DDoS高防|√|○|服务级别|-   AliyunYundunHighFullAccess
-   AliyunYundunHighReadOnlyAccess

|-|
|游戏盾|√|○|服务级别|-   AliyunYundunGameShieldReadOnlyAccess
-   AliyunYundunGameShieldFullAccess

|-|
|Web应用防火墙（网络安全）|√|○|服务级别|-   AliyunYundunWAFFullAccess
-   AliyunYundunWAFReadOnlyAccess

|-|
|SSL证书（应用安全）|√|○|服务级别|-   AliyunYundunCertFullAccess
-   AliyunYundunCertReadOnlyAccess

|-|
|风险识别（业务安全）|√|○|服务级别|-   AliyunYundunSAFFullAccess
-   AliyunYundunSAFReadOnlyAccess

|-|
|先知（安全服务）|√|○|服务级别|-   AliyunYundunXianzhiFullAccess
-   AliyunYundunXianzhiReadOnlyAccess

|-|
|云防火墙|√|○|服务级别|-   AliyunYundunCloudFirewallReadOnlyAccess
-   AliyunYundunCloudFirewallFullAccess

|-|
|实人认证|√|○|服务级别|-   AliyunYundunCloudAuthReadOnlyAccess
-   AliyunYundunCloudAuthFullAccess

|-|
|漏洞扫描（应用安全）|√|○|服务级别|AliyunYundunAvdsFullAccess|-|
|安全管家（安全服务）|√|○|服务级别|-|-|
|加密服务（数据安全）|√|○|服务级别|-   AliyunYundunHSMFullAccess
-   AliyunYundunHSMReadOnlyAccess

|-|
|内容安全（业务安全）|√|○|服务级别|AliyunYundunGreenWebFullAccess|-|
|数据风控（业务安全）|√|○|服务级别|AliyunYundunAFSFullAccess|-|
|移动安全|√|○|服务级别|AliyunYundunJaqFullAccess|-|
|合作伙伴中心|√|○|服务级别|AliyunYundunPartnerFullAccess|-|
|数据库审计（数据安全）|√|○|服务级别|-   AliyunYundunDbAuditFullAccess
-   AliyunYundunDbAuditReadOnlyAccess

|-|
|堡垒机 （安全管理）|√|○|服务级别|-   AliyunYundunBastionHostFullAccess
-   AliyunYundunBastionHostReadOnlyAccess
-   AliyunYundunBastionHostOperateOnlyAccess
-   AliyunYundunBastionHostAuditOnlyAccess

|-|
|爬虫风险管理|√|○|服务级别|-   AliyunYundunAntibotFullAccess
-   AliyunYundunAntibotReadOnlyAccess

|-|
|敏感数据保护（数据安全）|√|○|服务级别|-   AliyunYundunSDDPFullAccess
-   AliyunYundunSDDPReadOnlyAccess

|-|
|金融级实人认证|√|○|服务级别|-   AliyunAntCloudAuthFullAccess
-   AliyunAntCloudAuthReadOnlyAccess

|-|
|应用身份服务|√|○|操作级别|-   AliyunYundunIdaasFullAccess
-   AliyunYundunIdaasReadOnlyAccess

|-|

## 云市场

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云市场|√|○|服务级别|AliyunMarketplaceFullAccess|-|

## 域名与网站

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|云解析DNS|√|○|资源级别|-   AliyunDNSFullAccess
-   AliyunDNSReadOnlyAccess

|-|
|域名|√|√|资源级别|AliyunDomainFullAccess|[Domain API鉴权规则](/cn.zh-CN/域名管理/RAM资源授权-域名/Domain API鉴权规则.md)|
|云虚拟主机|×|×|-|-|-|
|企业邮箱|×|×|-|-|-|
|标准建站|×|×|-|-|-|
|弹性Web托管|×|×|-|-|-|
|商标服务|×|×|-|-|-|
|工商财税|√|○|服务级别|-|-|
|计算机软件著作权登记|√|○|服务级别|-|-|
|IP地理位置库|√|√|资源级别|-   AliyunGeoipFullAccess
-   AliyunGeoipReadOnlyAccess

|[RAM鉴权]()|

## 会员服务

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|备案|√|○|服务级别|AliyunBeianFullAccess|-|

## 费用中心

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|费用中心|√|×|服务级别|-   AliyunBSSFullAccess
-   AliyunBSSReadOnlyAccess
-   AliyunBSSOrderAccess
-   AliyunBSSRefundAccess

|[费用中心RAM策略介绍](https://help.aliyun.com/document_detail/88883.html)

[API调用授权](https://help.aliyun.com/document_detail/139650.html) |

## 工单

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|工单|√|○|服务级别|AliyunSupportFullAccess|-|

## 消息

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|消息中心|√|○|服务级别|AliyunNotificationsFullAccess|-|

## 企业控制台

|服务名|控制台|API|授权粒度|系统策略|相关文档|
|:--|:--|:--|:---|:---|:---|
|财务管理|√|○|服务级别|-   AliyunFinanceConsoleReadOnlyAccess
-   AliyunFinanceConsoleFullAccess

|-|

