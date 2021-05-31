# Manage information about all resources within an Alibaba Cloud account except billing information

This topic describes how to authorize a RAM user to manage information about all cloud resources within an Alibaba Cloud account except billing information. This topic provides a policy as an example.

The following policy specifies that the authorized RAM user can manage information about all cloud resources within an Alibaba Cloud account except billing information.

```
{
    "Statement": [
        {
            "Action": "*",
            "Effect": "Allow",
            "Resource": "*"
        },
        {
            "Action": [
                "bss:*",
                "efc:*"
            ],
            "Effect": "Deny",
            "Resource": "*"
        }
    ],
    "Version": "1"
}
```

