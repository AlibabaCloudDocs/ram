# Authorize a RAM user to manage MFA devices

This topic describes how to authorize a Resource Access Management \(RAM\) user to manage multi-factor authentication \(MFA\) devices by using an example policy.

The following policy indicates that the authorized RAM user `alice` can enable and disable MFA devices.

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

If you want to authorize a specific RAM user in your Alibaba Cloud account to manage MFA devices, you can attach the policy to the RAM user. Unauthorized RAM users cannot manage MFA devices.

To authorize all the RAM users in your Alibaba Cloud account to manage MFA devices, perform the following steps: Log on to the RAM console. In the left-side navigation pane, choose Identities \> Settings. On the Settings page, click Update RAM User Security Settings in the RAM User Security section. In the Update RAM User Security Settings panel, set **Manage MFA Devices** to **Allowed**. For more information, see [Set security policies for RAM users](/intl.en-US/Security Settings/Basic security settings/Set security policies for RAM users.md).

