# View information about all cloud resources within an Alibaba Cloud account except billing information

This topic describes how to authorize a Resource Access Management \(RAM\) user to view information about all cloud resources within an Alibaba Cloud account except billing information. This topic provides a policy as an example.

The following policy specifies that the authorized RAM user can view information about all cloud resources within an Alibaba Cloud account except billing information.

```
{
    "Version": "1",
    "Statement": [
        {
            "Action": [
                "*:Describe*",
                "*:List*",
                "*:Get*",
                "*:BatchGet*",
                "*:Query*",
                "*:BatchQuery*",
                "actiontrail:LookupEvents",
                "dm:Desc*",
                "dm:SenderStatistics*"
            ],
            "Resource": "*",
            "Effect": "Allow"
        },
    {
            "Action": [
                "bss:*",
                "efc:*"
            ],
            "Effect": "Deny",
            "Resource": "*"
        }

    ]
}
```

