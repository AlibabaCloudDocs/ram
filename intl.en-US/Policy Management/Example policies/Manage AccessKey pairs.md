# Manage AccessKey pairs

This topic uses an example policy to demonstrate how to authorize a RAM user to manage AccessKey pairs.

The following policy indicates that the authorized RAM user \(`alice`\) can create, delete, and update AccessKey pairs.

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

You can attach the policy to RAM users if you need to authorize the RAM users to manage their own AccessKey pairs. Unauthorized RAM users cannot manage their AccessKey pairs.

To allow all RAM users under the Alibaba Cloud account to manage their own AccessKey pairs, perform the following steps: Log on to the RAM console and choose **Identities** \> **Settings** \> **Update RAM User Security Settings**. In the pane that appears, select **Allowed** under **Manage AccessKey**. For more information, see [Set security policies for RAM users](/intl.en-US/Security Settings/Basic security settings/Set security policies for RAM users.md).

