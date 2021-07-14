# Use RAM to manage CDN permissions

This topic describes how to manage Alibaba Cloud CDN \(CDN\) permissions of Resource Access Management \(RAM\) users. In the RAM console, you can create custom policies and attach them to the RAM users.

-   Before you manage the CDN permissions of RAM users, take note of the following system policies:

    -   AliyunCDNFullAccess: grants a RAM user the permissions to manage CDN.
    -   AliyunCDNReadOnlyAccess: grants a RAM user the read-only permission on CDN.
    If the system policies cannot meet your business requirements, you can create custom policies.

-   Before you manage the CDN permissions of RAM users, take note of the CDN permissions. For more information, see [RAM authentication](/intl.en-US/API Reference/RAM authentication.md).

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md).

    The following custom policy indicates that RAM users are authorized to perform CDN read-only, cache refresh, and preload operations. You can modify the policy content to grant different permissions to RAM users. For more information about how to use the `Action` or `Resource` elements, see [Policy elements](/intl.en-US/Policy Management/Policy language/Policy elements.md).

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "cdn:Describe*",
            "cdn:PushObjectCache",
            "cdn:RefreshObjectCaches"
          ],
          "Resource": "acs:cdn:*:*:*",
          "Effect": "Allow"
        }
      ]
    }
    ```

3.  Attach the policy to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


