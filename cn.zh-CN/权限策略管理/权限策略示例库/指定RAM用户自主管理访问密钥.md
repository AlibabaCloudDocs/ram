# 指定RAM用户自主管理访问密钥

本文为您提供指定RAM用户自主管理访问密钥（AccessKey）的参考示例。

下述策略表示：RAM用户`alice`可以自主管理AccessKey，包括创建AccessKey、删除AccessKey以及更新AccessKey的状态等。

```
{
  "Version": "1",
  "Statement": [
    {
      "Action": [
      "ram:CreateAccessKey",
      "ram:ListAccessKeys",
      "ram:UpdateAccessKey",
      "ram:DeleteAccessKey"
      ],
      "Resource": "acs:ram:*:*:user/alice",
      "Effect": "Allow"
    }
  ]
}
```

该权限策略适用于：仅允许阿里云账号下指定RAM用户自主管理AccessKey，其他RAM用户不需要自主管理AccessKey的场景。

如果允许阿里云账号下所有RAM用户都自主管理AccessKey，请登录RAM控制台，修改RAM用户安全设置，将**自主管理AccessKey**设置为**允许**。具体操作，请参见[设置RAM用户安全策略](/cn.zh-CN/安全设置/基本安全设置/设置RAM用户安全策略.md)。

