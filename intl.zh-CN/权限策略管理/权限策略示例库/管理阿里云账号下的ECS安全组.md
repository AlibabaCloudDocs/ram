# 管理阿里云账号下的ECS安全组

本文为您提供管理阿里云账号下ECS安全组的参考示例。

下述策略表示：您拥有管理阿里云账号下ECS安全组的权限。

```
{
  "Version": "1",
  "Statement": [
    {
      "Action": "ecs:*SecurityGroup*",
      "Resource": "*",
      "Effect": "Allow"
    }
  ]
}
```

