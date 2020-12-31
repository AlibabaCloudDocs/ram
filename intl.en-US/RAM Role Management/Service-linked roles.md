# Service-linked roles

A trusted Alibaba Cloud service can assume a Resource Access Management \(RAM\) role to access other Alibaba Cloud services. RAM roles that a trusted Alibaba Cloud service can assume are classified into two types: normal service role and service-linked role. This topic describes service-linked roles.

## What is a service-linked role?

An Alibaba Cloud service may need to access other services to implement a feature. In this case, the Alibaba Cloud service must be authorized. For example, to retrieve resource lists and log data from Elastic Compute Service \(ECS\) and ApsaraDB RDS, Cloud Config requires the access permissions on ECS and RDS. Alibaba Cloud provides service-linked roles to simplify the authorization in such scenarios.

A service-linked role is a RAM role that only the linked service can assume. In most cases, a service automatically creates or deletes a service-linked role if needed. The service-linked role simplifies the process to authorize a service to access other services and reduces the risks caused by user errors.

The policy that is attached to a service-linked role is predefined by the linked service. You cannot modify or delete the policy. In addition, you cannot attach policies to or detach policies from a service-linked role.

If a service does not support service-linked roles, you can use a normal service role to authorize the service.

## Create a service-linked role

Some Alibaba Cloud services automatically create service-linked roles when you perform operations such as creating a cloud resource or enabling a feature. You can view the created service-linked roles on the RAM Roles page of the RAM console. You can also retrieve a list of created service-linked roles by using the API or CLI to call the ListRoles operation.

You can also manually create service-linked roles. For more information, see [Create a service linked role](/intl.en-US/RAM Role Management/Create a RAM role/Create a RAM role for a trusted Alibaba Cloud service.md).

**Note:**

-   Service-linked roles count toward the limit of RAM roles of your Alibaba Cloud account. If the limit is exceeded, you can still create service-linked roles but you can no longer create RAM roles of other types.
-   For more information about how an Alibaba Cloud service creates a service-linked role, see the documentation that is specific to the service.

## Delete the service-linked role AliyunServiceRoleForDAS

Some Alibaba Cloud services automatically delete service-linked roles when you perform operations such as deleting a cloud resource or disabling a feature. You can also manually delete service-linked roles in the RAM console. For more information about how to delete a service-linked role, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

When you attempt to delete a service-linked role, RAM first checks whether the role is being assumed by the linked service.

-   If the service-linked role is idle, it is deleted.
-   If the service-linked role is in use, it cannot be deleted. However, you can view the service resources that assume the service-linked role. If you no longer need the service resources, find and remove the resources, and then delete the service-linked role.

**Note:** For more information about the conditions that allow you to delete a service-linked role, see the documentation that is specific to the linked service.

## Permissions required to create and delete a service-linked role

RAM identities must be granted the required permissions before they can create or delete a service-linked role. The permissions are also required in scenarios where service-linked roles are automatically created when RAM identities perform operations.

**Note:** The permission to create a service-linked role is included in the administrative permission policy of the linked service \(for example, AliyunESSFullAccess of ECS\). Therefore, after you attach the administrative permission policy of a service to a RAM identity, the RAM identity is allowed to create the service-linked role for the service.

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

A service-linked role can be assumed by only the linked service and cannot be assumed by identities such as RAM users or other RAM roles.

You can view the service that can assume a service-linked role in the `Service` element on the Trust Policy Management tab of the role details page.

## Alibaba Cloud services that support service-linked roles

|Alibaba Cloud service|The name of the service|Service-linked role|Reference|
|---------------------|-----------------------|-------------------|---------|
|Resource Management|resourcemanager.aliyuncs.com|AliyunServiceRoleForResourceDirectory|[Service linked role for Resource Directory]()|
|Cloud Config|config.aliyuncs.com|AliyunServiceRoleForConfig|[Manage the service linked role associated with Cloud Config](/intl.en-US/Quick Start/Manage the service linked role associated with Cloud Config.md)|
|PolarDB|polardb.aliyuncs.com|AliyunServiceRoleForPolarDB|[RAM role linked to Apsara PolarDB](/intl.en-US/API Reference/RAM role linked to Apsara PolarDB.md)|
|Hybrid Backup Recovery \(HBR\)|dr.hbr.aliyuncs.com|AliyunServiceRoleForHbrDr|[Service linked role for ECS disaster recovery](/intl.en-US/Disaster Recovery/ECS Disaster Recovery/Service linked role for ECS disaster recovery.md)|
|Operation Orchestration Service \(OOS\)|bandwidthscheduler.oos.aliyuncs.com|AliyunServiceRoleForOOSBandwidthScheduler|[OOS linked roles]()|
|instancescheduler.oos.aliyuncs.com|AliyunServiceRoleForOOSInstanceScheduler|
|Auto Scaling \(ESS\)|ess.aliyuncs.com|AliyunServiceRoleForAutoScaling|[Grant permissions to Auto Scaling]()|
|Time Series Database \(TSDB\)|hitsdb.aliyuncs.com|AliyunServiceRoleForTSDB|N/A |
|Cloud Monitor|cloudmonitor.aliyuncs.com|AliyunServiceRoleForCloudMonitor|[Manage the service linked role for CloudMonitor](/intl.en-US/Appendix 3 account authorization/Manage the service linked role for CloudMonitor.md)|
|Blockchain as a Service \(BaaS\)|baas.aliyuncs.com|AliyunServiceRoleForBaaS|N/A |
|Global Traffic Manager|gtm.aliyuncs.com|AliyunServiceRoleForGTM|[Service-linked role of Global Traffic Manager]()|
|Alibaba Cloud DNS \(DNS\)|alidns.aliyuncs.com|AliyunServiceRoleForDNS|N/A |
|Sensitive Data Discovery and Protection|sddp.aliyuncs.com|AliyunServiceRoleForSDDP|[Authorize SDDP to access Alibaba Cloud resources](/intl.en-US/User Guide/Authorize SDDP to access Alibaba Cloud resources.md)|
|CDN|cdn-ddos.cdn.aliyuncs.com|AliyunServiceRoleForCDNAccessingDDoS|[Configure Anti-DDoS](/intl.en-US/Domain Management/Security configuration/Integrate Alibaba Cloud CDN with Anti-DDoS.md)|

