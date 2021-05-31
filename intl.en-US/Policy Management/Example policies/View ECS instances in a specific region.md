# View ECS instances in a specific region

This topic describes how to authorize a Resource Access Management \(RAM\) user to view Elastic Compute Service \(ECS\) instances in a specific region. A policy is used as an example in this topic.

The following policy indicates that the authorized RAM user can view ECS instances in the China \(Qingdao\) region, but cannot view disks or snapshots in this region.

```
{
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ecs:Describe*",
      "Resource": "acs:ecs:cn-qingdao:*:instance/*"
    }
  ],
  "Version": "1"
}
```

**Note:** You can grant permissions on ECS instances to the RAM user based on the region and resource type. If you want to authorize a RAM user or role to view ECS instances in another region, you can change `cn-qingdao` in the `Resource` element to the ID of the required region. For more information about region IDs, see [Regions and zones]().

