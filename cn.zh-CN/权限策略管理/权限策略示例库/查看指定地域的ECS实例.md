# 查看指定地域的ECS实例

本文为您提供查看指定地域ECS实例的参考示例。

以下策略表示：仅允许您查看青岛的ECS实例，但不允许查看磁盘及快照。

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

**说明：** 查看ECS资源列表的授权粒度可以到地域+资源类型的级别，如果您想授权RAM用户或RAM角色查看其他地域的ECS实例，您可以将`Resource`中的`cn-qingdao`替换为其他地域ID。关于地域ID，详情请参见[地域和可用区]()。

