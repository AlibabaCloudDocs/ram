# Manage ECS security groups within an Alibaba Cloud account

This topic describes how to authorize a Resource Access Management \(RAM\) user to manage Elastic Compute Service \(ECS\) security groups within an Alibaba Cloud account. This topic provides a policy as an example.

The following policy specifies that the authorized RAM user can manage ECS security groups within an Alibaba Cloud.

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

