# Access Alibaba Cloud resources by using a specific IP address or CIDR block

This topic provides a sample policy that you can use to authorize your Resource Access Management \(RAM\) users. This policy allows RAM users to access Alibaba Cloud resources by using a specific IP address or Classless Inter-Domain Routing \(CIDR\) block.

In the following code, the RAM users can access Elastic Cloud Service \(ECS\) instances only by using 172.16.215.218 and 192.168.0.0/16.

You must specify `acs:SourceIp` in `Condition`, as shown in the following code.

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
         ]
        }
      }
    }
  ],
  "Version": "1"
}
```

**Note:**

-   `Condition` is applicable only to the actions that are specified in the policy.
-   The value of `acs:SourceIp` in the preceding code is only for reference. You must specify the value based on your business requirements.

