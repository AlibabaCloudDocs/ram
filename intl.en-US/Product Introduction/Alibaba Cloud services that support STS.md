# Alibaba Cloud services that support STS

This topic lists the Alibaba Cloud services that support Security Token Service \(STS\).

## Overview

You can query Alibaba Cloud services that support STS based on the following categories:

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

-   Alibaba Cloud service: the name of the cloud service that supports STS.
-   Sub-service/Sub-module: the sub-service or sub-module of the cloud service. "-" indicates none.
-   Console: indicates whether RAM can be used to implement access control in the console of the service. A check sign \(✓\) indicates that RAM is supported. A cross sign \(×\) indicates that RAM is not supported. A circle \(○\) indicates that no console is provided for that service.
-   API: indicates whether STS can be used to implement access control when you call the API of the service. A check sign \(✓\) indicates that STS is supported when you call the API of the service. A cross sign \(×\) indicates that STS is not supported when you call the API of the service. A circle \(○\) indicates that no API is provided for that service.

For more information about STS, see [What is STS?](/intl.en-US/API Reference/API Reference (STS)/What is STS?.md) and [RAM role overview](/intl.en-US/RAM Role Management/RAM role overview.md).

## Elastic computing

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Elastic Compute Service \(ECS\)|ECS|✓|✓|
|ECS|Elastic Block Storage \(EBS\)|✓|✓|
|ECS|Elastic GPU Service|✓|✓|
|ECS|ECS Bare Metal Instance|✓|✓|
|ECS|Super Computing Cluster|✓|✓|
|ECS|Dedicated Host \(DDH\)|✓|✓|
|ECS|Alibaba Cloud Linux 2|✓|✓|
|Auto Scaling \(ESS\)|-|✓|✓|
|Container Service for Kubernetes \(ACK\)|-|✓|✓|
|Batch Compute|-|✓|✓|
|Resource Orchestration Service \(ROS\)|-|✓|✓|
|Function Compute|-|✓|✓|
|Simple Application Server|-|×|○|
|Elastic High Performance Computing \(E-HPC\)|-|✓|✓|
|Container Registry|-|✓|✓|
|Elastic Cloud Desktop|Elastic Desktop Service \(EDS\)|✓|✓|
|Elastic Container Instance \(ECI\)|-|✓|✓|
|Serverless Workflow|-|✓|✓|
|Web App Service|-|✓|✓|

## Database

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|ApsaraDB RDS|ApsaraDB RDS|✓|✓|
|ApsaraDB RDS|ApsaraDB RDS for MySQL|✓|✓|
|ApsaraDB RDS|ApsaraDB RDS for SQL Server|✓|✓|
|ApsaraDB RDS|ApsaraDB RDS for PostgreSQL|✓|✓|
|ApsaraDB RDS|ApsaraDB RDS for PPAS|✓|✓|
|ApsaraDB RDS|ApsaraDB for MyBase|✓|✓|
|ApsaraDB for Redis|-|✓|✓|
|ApsaraDB for Memcache|-|✓|✓|
|ApsaraDB for MongoDB|-|✓|✓|
|AnalyticDB for PostgreSQL|-|✓|✓|
|Data Transmission Service \(DTS\)|-|✓|✓|
|Data Management \(DMS\)|-|✓|✓|
|AnalyticDB for MySQL|-|✓|✓|
|PolarDB-X|-|✓|✓|
|ApsaraDB for HBase|-|✓|✓|
|Advanced Database & Application Migration \(ADAM\)|-|✓|○|
|PolarDB|-|✓|✓|
|Database Backup|-|✓|✓|
|Database Autonomy Service|-|✓|✓|
|Data Lake Analytics \(DLA\)|-|✓|✓|
|ApsaraDB for OceanBase|-|✓|○|
|ApsaraDB for Cassandra|-|✓|✓|
|LedgerDB|-|✓|✓|
|ApsaraDB for ClickHouse|-|✓|✓|
|Database Gateway|-|✓|✓|

## Storage

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Object Storage Service \(OSS\)|-|✓|✓|
|Apsara File Storage NAS \(NAS\)|-|✓|✓|
|Tablestore|-|✓|✓|
|Cloud Storage Gateway \(CSG\)|-|✓|✓|
|Hybrid Backup Recovery \(HBR\)|-|✓|○|
|Hybrid Cloud Storage Array \(CSA\)|-|×|○|

## Cloud communications

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Short Message Service \(SMS\)|-|✓|✓|

## Networking

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Virtual Private Cloud \(VPC\)|-|✓|✓|
|Server Load Balancer \(SLB\)|Server Load Balancer \(SLB\)|✓|✓|
|Server Load Balancer \(SLB\)|Application Load Balancer \(ALB\)|✓|✓|
|Express Connect|-|✓|✓|
|Elastic IP Address \(EIP\)|-|✓|✓|
|NAT Gateway \(NAT\)|-|✓|✓|
|VPN Gateway|-|✓|✓|
|EIP Bandwidth Plan|-|✓|✓|
|Global Accelerator \(GA\)|-|✓|✓|
|Smart Access Gateway \(SAG\)|-|✓|✓|
|Cloud Enterprise Network \(CEN\)|-|✓|✓|
|PrivateLink|-|✓|✓|
|Alibaba Cloud DNS PrivateZone|-|✓|✓|

## O&M management

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Application Real-Time Monitoring Service \(ARMS\)|-|×|×|
|CloudMonitor|-|✓|✓|
|Cloud Shell|-|×|○|
|Cloud Config|-|✓|✓|
|Logic Composer|-|✓|✓|
|Operation Orchestration Service \(OOS\)|-|✓|✓|

## Middleware

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Enterprise Distributed Application Service \(EDAS\)|-|×|✓|
|Message Queue|Message Queue for Apache RocketMQ|✓|✓|
|Message Queue|Message Queue for MQTT|✓|✓|
|Message Queue|Message Queue for RabbitMQ|✓|✓|
|Message Service \(MNS\)|-|✓|✓|
|Application Configuration Management|-|✓|✓|
|Message Queue for Apache Kafka|-|✓|✓|
|Application High Availability Service|-|✓|×|
|Alibaba Cloud Service Mesh \(ASM\)|-|✓|✓|
|EventBridge|-|✓|✓|

## Media services and CDN

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|CDN|-|✓|✓|
|ApsaraVideo for Media Processing \(MTS\)|-|✓|✓|
|ApsaraVideo VOD \(VOD\)|-|✓|✓|
|ApsaraVideo for Live|-|✓|✓|
|Real-Time Communication|-|✓|✓|
|Dynamic Route for CDN \(DCDN\)|-|✓|✓|

## Enterprise applications

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Direct Mail|-|✓|✓|
|API Gateway|-|✓|✓|
|Resource Management|Resource Management|✓|✓|
|Resource Management|Tag|✓|✓|
|Blockchain as a Service \(BaaS\)|Blockchain as a Service \(BaaS\)|✓|✓|
|CloudQuotation \(CQ\)|-|✓|○|

## Domains and websites

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Alibaba Cloud DNS \(DNS\)|Alibaba Cloud DNS \(DNS\)|✓|✓|
|Alibaba Cloud DNS \(DNS\)|Alibaba Cloud Public DNS|✓|✓|
|Domains|-|✓|✓|

## Artificial intelligence

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Intelligent Speech Interaction|-|×|×|
|Machine Learning Platform for AI \(PAI\)|-|×|×|
|Image Search|-|✓|✓|
|Machine Translation|-|×|×|

## IoT

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|IoT Platform|-|✓|✓|
|Link IoT Edge|-|×|×|
|ApsaraDB for Lindorm|Time Series Database \(TSDB\)|✓|✓|

## Big data

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|DataWorks|-|✓|✓|
|Quick BI|-|×|×|
|DataV|-|✓|○|
|Realtime Compute for Apache Flink|-|×|×|
|Elasticsearch|-|✓|✓|
|E-MapReduce|-|✓|✓|
|Log Service|-|✓|✓|
|Hologres|-|✓|✓|

## Developer services

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Apsara DevOps|-|×|×|
|Tracing Analysis|-|✓|✓|

## Security

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Security Center \(SAS\)|-|✓|✓|
|Server Guard|-|✓|✓|
|Anti-DDoS|Anti-DDoS|✓|✓|
|Anti-DDoS|Anti-DDoS Pro|✓|✓|
|Anti-DDoS|Anti-DDoS Premium|✓|✓|
|GameShield|-|✓|○|
|Web Application Firewall \(WAF\)|Web Application Firewall \(WAF\)|✓|✓|
|SSL Certificates Service|-|✓|✓|
|Cloud Firewall \(CFW\)|-|✓|✓|
|Managed Security Service \(MSSP\)|-|✓|○|
|Content Moderation|-|✓|✓|
|Bastionhost|Bastionhost|×|○|
|Data Security Center \(DSC\)|-|✓|✓|
|Identity as a Service \(IDaaS\)|-|✓|○|
|Key Management Service \(KMS\)|-|✓|✓|
|Resource Access Management \(RAM\)|-|✓|✓|
|ActionTrail|-|✓|✓|

## Technical support

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Ticket Management|-|✓|✓|

## Marketplace

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Alibaba Cloud Marketplace|-|✓|×|

## Others

|Alibaba Cloud service|Sub-service/Sub-module|Console|API|
|:--------------------|----------------------|:------|:--|
|Billing Management|-|✓|✓|
|ICP Filing|-|✓|○|

