# Policy models

Alibaba Cloud allows you to grant RAM identities the permissions to manage the resources of an Alibaba Cloud account or a resource group. You can select a policy model from these two options based on your business requirements.

## Manage the resources of an Alibaba Cloud account

In this model, if you attach a policy to a RAM identity, all Alibaba Cloud resources of the Alibaba Cloud account are included in the scope of the policy permissions.

![Manage the resources of an Alibaba Cloud account](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8487769751/p14311.png)

## Manage the resources of a resource group

[Resource Group]() authorization: In this model, if you attach a policy to a RAM identity, only the Alibaba Cloud resources of the resource group are included in the scope of the policy permissions.

Administrator: The RAM user that is attached with the `AdministratorAccess` system policy in a resource group is the administrator of the resource group. By default, the RAM user that creates the resource group is the administrator. The administrator can add RAM users to the resource group and grant permissions to the RAM users in the resource group.

![Manage the resources of a resource group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8487769751/p14312.png)

