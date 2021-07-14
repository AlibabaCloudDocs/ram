# Authorize a RAM user to manage AccessKey pairs

This topic describes how to authorize a Resource Access Management \(RAM\) user to manage AccessKey pairs by using an example policy.

The following policy indicates that the authorized RAM user `alice` can update the status of, create, and delete AccessKey pairs.

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

If you want to authorize a specific RAM user in your Alibaba Cloud account to manage its own AccessKey pairs, you can attach the policy to the RAM user.

To authorize all the RAM users in your Alibaba Cloud account to manage their own AccessKey pairs, perform the following steps: Log on to the RAM console. In the left-side navigation pane, choose Identities \> Settings. On the Settings page, click Update RAM User Security Settings in the RAM User Security section. In the Update RAM User Security Settings panel, set **Manage AccessKey** to **Allowed**. For more information, see [Set security policies for RAM users](/intl.en-US/Security Settings/Basic security settings/Set security policies for RAM users.md).

