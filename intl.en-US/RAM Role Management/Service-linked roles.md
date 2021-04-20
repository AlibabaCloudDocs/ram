# Service-linked roles

A trusted Alibaba Cloud service can assume a Resource Access Management \(RAM\) role to access other Alibaba Cloud services. RAM roles that a trusted Alibaba Cloud service can assume are classified into two types: normal service role and service-linked role. This topic describes service-linked roles.

## Background information

An Alibaba Cloud service may need to access other services to implement a feature. In this case, the Alibaba Cloud service must be authorized to access other services. For example, to retrieve resource lists and log data from Elastic Compute Service \(ECS\) and ApsaraDB RDS, Cloud Config requires the access permissions on ECS and ApsaraDB RDS. Alibaba Cloud provides service-linked roles to simplify the process to authorize a service to access other services.

A service-linked role is a RAM role that only the linked service can assume. In most cases, a service automatically creates or deletes the service-linked role if needed. A service-linked role simplifies the process to authorize a service to access other services and reduces the risks caused by misoperations.

The policy that is attached to a service-linked role is predefined by the linked service. You cannot modify or delete the policy. You cannot attach policies to or detach policies from a service-linked role.

If a service does not support service-linked roles, you can use a basic service role to authorize the service.

## Create a service-linked role

Some Alibaba Cloud services automatically create service-linked roles when you perform operations, for example, create a cloud resource or enable a feature. You can view the created service-linked roles on the RAM Roles page of the RAM console. You can also retrieve the list of created service-linked roles by using OpenAPI Explorer or Alibaba Cloud CLI to call the ListRoles operation.

You can also manually create service-linked roles. For more information, see [Create a service linked role](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md).

**Note:**

-   The number of service-linked roles that you can create is based on the limit of the number of RAM roles that you can create within your Alibaba Cloud account. If the limit is exceeded, you can still create service-linked roles. However, you can no longer create other types of RAM roles.
-   For more information about how an Alibaba Cloud service creates a service-linked role, see the documentation of the linked service.

## Delete a service-linked role

Some Alibaba Cloud services automatically delete service-linked roles when you perform operations, for example, delete a cloud resource or disable a feature. You can also manually delete service-linked roles in the RAM console. For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

If you attempt to delete a service-linked role, RAM checks whether the role is being assumed by the linked service.

-   If the role is not being assumed, it can be deleted.
-   If the role is being assumed, it cannot be deleted. However, you can view the cloud resources of the linked service that assume the service-linked role. If you no longer need the cloud resources of the linked service, find and remove the resources of the linked service, and then delete the service-linked role.

**Note:** For more information about the conditions that allow you to delete a service-linked role, see the documentation of the linked service.

## Permissions required to create and delete a service-linked role

RAM identities must be granted the required permissions before the RAM identities can create or delete a service-linked role. The permissions are also required in scenarios in which service-linked roles are automatically created.

**Note:** The permissions to create a service-linked role are included in the administrative permission policy of the linked service. For ECS, the administrative permission policy is AliyunESSFullAccess. If you attach the administrative permission policy of a service to a RAM identity, the RAM identity can create the service-linked role for the service.

The following sample policy allows authorized RAM identities to create and delete the service-linked role for Resource Management:

```
{
    "Action": [
        "ram:CreateServiceLinkedRole",
        "ram:DeleteServiceLinkedRole"
    ],
    "Resource": "*",
    "Effect": "Allow",
    "Condition": {
        "StringEquals": {
            "ram:ServiceName": "resourcemanager.aliyuncs.com"
        }
    }
}
```

## Assume a service-linked role

A service-linked role can be assumed only by the linked service. The role cannot be assumed by identities such as RAM users or other RAM roles.

You can view the service that can assume a service-linked role in the `Service` parameter on the Trust Policy Management tab of the role details page.

## Alibaba Cloud services that support service-linked roles

|Alibaba Cloud service|Code|Service-linked role|Documentation|
|---------------------|----|-------------------|-------------|
|Resource Management|resourcemanager.aliyuncs.com|AliyunServiceRoleForResourceDirectory|[Service linked role for Resource Directory]()|
|Cloud Config|config.aliyuncs.com|AliyunServiceRoleForConfig|[Manage the service linked role associated with Cloud Config](/intl.en-US/Permission Management/Manage the service linked role associated with Cloud Config.md)|
|remediation.config.aliyuncs.com|AliyunServiceRoleForConfigRemediation|
|PolarDB|polardb.aliyuncs.com|AliyunServiceRoleForPolarDB|[RAM role linked to Apsara PolarDB](/intl.en-US/API Reference/RAM role linked to Apsara PolarDB.md)|
|Hybrid Backup Recovery \(HBR\)|dr.hbr.aliyuncs.com|AliyunServiceRoleForHbrDr|[Service linked role for ECS disaster recovery](/intl.en-US/Disaster Recovery/ECS Disaster Recovery/Service linked role for ECS disaster recovery.md)|
|ecsbackup.hbr.aliyuncs.com|AliyunServiceRoleForHbrEcsBackup|[Service-linked roles for HBR](/intl.en-US/Product Introduction/Service linked roles for HBR.md)|
|ossbackup.hbr.aliyuncs.com|AliyunServiceRoleForHbrOssBackup|
|nasbackup.hbr.aliyuncs.com|AliyunServiceRoleForHbrNasBackup|
|csgbackup.hbr.aliyuncs.com|AliyunServiceRoleForHbrCsgBackup|
|Operation Orchestration Service \(OOS\)|bandwidthscheduler.oos.aliyuncs.com|AliyunServiceRoleForOOSBandwidthScheduler|[OOS linked roles]()|
|instancescheduler.oos.aliyuncs.com|AliyunServiceRoleForOOSInstanceScheduler|
|executiondelivery.oos.aliyuncs.com|AliyunServiceRoleForOOSExecutionDelivery|
|Auto Scaling \(ESS\)|ess.aliyuncs.com|AliyunServiceRoleForAutoScaling|[Grant permissions to Auto Scaling]()|
|Time Series Database \(TSDB\)|hitsdb.aliyuncs.com|AliyunServiceRoleForTSDB|None |
|Cloud Monitor|cloudmonitor.aliyuncs.com|AliyunServiceRoleForCloudMonitor|[Manage the service-linked role for Cloud Monitor](/intl.en-US/Appendix 3 account authorization/Manage the service-linked role for Cloud Monitor.md)|
|Blockchain as a Service \(BaaS\)|baas.aliyuncs.com|AliyunServiceRoleForBaaS|None |
|Global Traffic Manager|gtm.aliyuncs.com|AliyunServiceRoleForGTM|[Service-linked roles for Global Traffic Manager]()|
|Alibaba Cloud DNS \(DNS\)|alidns.aliyuncs.com|AliyunServiceRoleForDNS|None |
|Data Security Center \(DSC\)|sddp.aliyuncs.com|AliyunServiceRoleForSDDP|[Authorize DSC to access Alibaba Cloud resources](/intl.en-US/User Guide/Authorize DSC to access Alibaba Cloud resources.md)|
|CDN|cdn-ddos.cdn.aliyuncs.com|AliyunServiceRoleForCDNAccessingDDoS|[Configure Anti-DDoS](/intl.en-US/Domain Management/Security configuration/Integrate Alibaba Cloud CDN with Anti-DDoS.md)|
|cdn-waf.cdn.aliyuncs.com|AliyunServiceRoleForCDNAccessingWAF|None|
|Application Real-Time Monitoring Service \(ARMS\)|arms.aliyuncs.com|AliyunServiceRoleForARMS|[Service linked role for ARMS](/intl.en-US/Access Control/Service linked role for ARMS.md)|
|EventBridge|sendevent-fc.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeSendToFC|[Service-linked roles for EventBridge]()|
|sendevent-mns.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeSendToMNS|
|sendevent-sms.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeSendToSMS|
|sendevent-directmail.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeSendToDirectMail|
|source-rocketmq.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeSourceRocketMQ|
|connect-vpc.eventbridge.aliyuncs.com|AliyunServiceRoleForEventBridgeConnectVPC|
|DataWorks|di.dataworks.aliyuncs.com|AliyunServiceRoleForDataWorksDI|[Service linked role of DataWorks Data Integration]()|
|Elastic High Performance Computing \(E-HPC\)|ehpc.aliyuncs.com|AliyunServiceRoleForEHPC|[Service-linked roles for E-HPC](https://www.alibabacloud.com/help/zh/doc-detail/186678.htm)|
|Server Migration Center \(SMC\)|smc.aliyuncs.com|AliyunServiceRoleForSMC|[Service linked roles for SMC](/intl.en-US/API Reference/Service linked roles for SMC.md)|
|Message Queue for Apache Kafka|connector.alikafka.aliyuncs.com|AliyunServiceRoleForAlikafkaConnector|[Service-linked roles for Message Queue for Apache Kafka](/intl.en-US/Access control/Service-linked roles.md)|
|instanceencryption.alikafka.aliyuncs.com|AliyunServiceRoleForAlikafkaInstanceEncryption|
|Tracing Analysis|xtrace.aliyuncs.com|AliyunServiceRoleForXtrace|[Service linked role for Tracing Analysis](/intl.en-US/RAM/Service linked role for Tracing Analysis.md)|
|NAT Gateway \(NAT\)|nat.aliyuncs.com|AliyunServiceRoleForNatgw|[Service-linked roles for NAT Gateway](/intl.en-US/Common Configurations/Service-linked roles for NAT Gateway.md)|
|Alibaba Cloud DNS PrivateZone|pvtz.aliyuncs.com|AliyunServiceRoleForPvtz|[Service-linked roles for Alibaba Cloud DNS PrivateZone](https://www.alibabacloud.com/help/zh/doc-detail/175951.htm)|
|ActionTrail|actiontrail.aliyuncs.com|AliyunServiceRoleForActionTrail|[Manage the service linked role](/intl.en-US/Permission Management/Manage the service linked role.md)|
|Cloud Storage Gateway \(CSG\)|hcs-sgw.aliyuncs.com|AliyunServiceRoleForHCSSGW|[Service-linked roles for CSG](/intl.en-US/Overview/Service linked roles for CSG.md)|
|logmonitor.hcs-sgw.aliyuncs.com|AliyunServiceRoleForHCSSGWLogMonitor|
|Data Lake Analytics \(DLA\)|openanalytics.aliyuncs.com|AliyunServiceRoleForOpenAnalytics|[AliyunServiceRoleForOpenAnalytics]()|
|API Gateway|apigateway.aliyuncs.com|AliyunServiceRoleForApiGateway|None |
|monitor.apigateway.aliyuncs.com|AliyunServiceRoleForApiGatewayMonitoring|None |
|Elasticsearch|ops.elasticsearch.aliyuncs.com|AliyunServiceRoleForElasticsearchOps|None |
|collector.elasticsearch.aliyuncs.com|AliyunServiceRoleForElasticsearchCollector|
|Bastionhost|bastionhost.aliyuncs.com|AliyunServiceRoleForBastionhost|[Service linked role for Bastionhost](/intl.en-US/User Guide (V3.2)/Administrator manual/Authorize Bastionhost to access cloud resources.md)|
|Global Accelerator \(GA\)|vpcendpoint.ga.aliyuncs.com|AliyunServiceRoleForGaVpcEndpoint|[AliyunServiceRoleForGaVpcEndpoint](/intl.en-US/User Guide/Service-linked role/AliyunServiceRoleForGaVpcEndpoint.md)|
|ddos.ga.aliyuncs.com|AliyunServiceRoleForGaAntiDdos|None|
|Message Queue for Apache RocketMQ|ons.aliyuncs.com|AliyunServiceRoleForOns|[Service-linked roles for Message Queue for Apache RocketMQ]()|
|AnalyticDB for PostgreSQL|adbpg.aliyuncs.com|AliyunServiceRoleForADBPG|[Service-linked roles for AnalyticDB for PostgreSQL](/intl.en-US/API Reference/Service linked role.md)|
|Key Management Service \(KMS\)|secretsmanager-rds.kms.aliyuncs.com|AliyunServiceRoleForKMSSecretsManagerForRDS|[Manage the service-linked role for dynamic ApsaraDB RDS secrets](/intl.en-US/Secrets Manager/Dynamic ApsaraDB RDS secrets/Manage the service-linked role for dynamic ApsaraDB RDS secrets.md)|

