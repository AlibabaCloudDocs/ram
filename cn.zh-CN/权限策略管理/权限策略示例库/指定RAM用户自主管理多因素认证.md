# 指定RAM用户自主管理多因素认证

本文为您提供指定RAM用户自主管理多因素认证（MFA）的参考示例。

下述策略表示：RAM用户`alice`可以自主管理MFA，包括绑定MFA和解绑MFA。

```
{
   "Statement": [
       {
           "Action": [
               "ram:GetUserMFAInfo",
               "ram:BindMFADevice",
               "ram:UnbindMFADevice"
           ],
           "Resource": "acs:ram:*:*:user/alice",
           "Effect": "Allow"
       },
       {
           "Action": [
               "ram:CreateVirtualMFADevice",
               "ram:DeleteVirtualMFADevice"
           ],
           "Resource": "*",
           "Effect": "Allow"
       }
   ],
   "Version": "1"
}
```

该权限策略适用于：仅允许阿里云账号下指定RAM用户自主管理多因素认证（MFA），其他RAM用户不需要自主管理多因素认证（MFA）的场景。

如果允许阿里云账号下所有RAM用户都自主管理多因素认证（MFA），请登录RAM控制台，修改RAM用户安全设置，将**自主管理多因素设备**设置为**允许**。具体操作，请参见[设置RAM用户安全策略](/cn.zh-CN/安全设置/基本安全设置/设置RAM用户安全策略.md)。

