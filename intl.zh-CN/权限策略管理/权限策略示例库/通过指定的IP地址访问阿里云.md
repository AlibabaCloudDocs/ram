# 通过指定的IP地址访问阿里云

本文为您提供RAM用户通过指定IP地址访问阿里云的策略样例。

RAM用户只能通过192.168.0.0/16和172.16.215.218这两个IP地址访问ECS。

您可以通过设置`Condition`下`acs:SourceIp`的值来实现。

```
{
  "Statement": [
    {
      "Action": "ecs:*",
      "Effect": "Allow",
      "Resource": "*",
      "Condition": {
        "IpAddress": {
          "acs:SourceIp":[
		  "192.168.0.0/16",
		  "172.16.215.218"
        }
      }
    }
  ],
  "Version": "1"
}
```

**说明：**

-   `Condition`（限制条件）只针对当前权限策略描述的操作有效。
-   请将`acs:SourceIp`的值修改为您实际环境的真实IP地址。

