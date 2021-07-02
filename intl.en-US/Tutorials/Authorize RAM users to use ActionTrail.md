# Authorize RAM users to use ActionTrail

This topic shows you how to create custom policies to grant permissions to the RAM users within your Alibaba Cloud account. Then, you can log on to the ActionTrail console as one of these RAM users and use ActionTrail resources.

-   Take note of the following system policies before you authorize RAM users to use ActionTrail:

    -   AliyunActionTrailFullAccess: full permissions on ActionTrail
    -   AliyunActionTrailReadOnlyAccess: read-only permissions on ActionTrail
    If the preceding system policies cannot meet your requirements, you can create custom policies as needed.

-   You must view the supported ActionTrail API operations and the RAM policies related to ActionTrail before the authorization. For more information, see [RAM account authentication](/intl.en-US/API Reference/API Reference (2017-12-04)/RAM account authentication.md).

## Procedure

1.  Create a RAM user.

    For more information, see [Create a RAM user](/intl.en-US/RAM User Management/Basic operations/Create a RAM user.md).

2.  Create a custom policy.

    For more information, see [Create a custom policy](/intl.en-US/Policy Management/Custom policies/Create a custom policy.md) and [Examples of policies](#section_xqm_lnm_xgb).

3.  Grant the required permissions to the RAM user.

    For more information, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).


## Examples of policies

-   Example 1: Grant read-only permissions on ActionTrail to a RAM user.

    ```
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*"
        }]
    }
                        
    ```

-   Example 2: Grant read-only permissions on ActionTrail to a RAM user and allow the RAM user to access ActionTrail only from a specified IP address.

    ```
    {
        "Version": "1",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
                "actiontrail:LookupEvents", 
                "actiontrail:Describe*", 
                "actiontrail:Get*"
            ],
            "Resource": "*",
            "Condition":{
                "IpAddress": {
                    "acs:SourceIp": "42.120.XX.X/24"
                }
            }
        }]
    }
    ```


