# Edit the trust policy of a RAM role

You can edit the policy that is attached to a Resource Access Management \(RAM\) role to change the trusted entity of the RAM role. This topic describes how to change the trusted entity of a RAM role to an Alibaba Cloud account, an Alibaba Cloud service, or an identity provider \(IdP\).

When you create a RAM role, you can specify an Alibaba Cloud account, an Alibaba Cloud service, or an IdP as the trusted entity of the RAM role. In most cases, you do not need to change the trusted entity after you create a RAM role. If you must change the trusted entity, you can use one of the methods described in this topic. After you change the trusted entity, you must check whether the RAM role functions as expected.

## Procedure

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the RAM Roles page, find the specific RAM role and click its name.

4.  Click the **Trust Policy Management** tab. On this tab, click **Edit Trust Policy**.

5.  In the Edit Trust Policy panel, modify the trust policy and click **OK**.


## Example 1: Change the trusted entity of a RAM role to an Alibaba Cloud account

If the `Principal` element in a policy includes the `RAM` field, the trusted entity is an **Alibaba Cloud account**. A RAM role to which the policy is attached can be assumed by authorized RAM users of the trusted Alibaba Cloud account.

In the following policy, the RAM role can be assumed by all the RAM users of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:root"
                ]
            }
        }
    ],
    "Version": "1"
}
```

If you configure the `Principal` element based on the following code, the RAM role can be assumed by the RAM user named `testuser` of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"
                ]
            }                   
```

**Note:** Before you edit the trust policy, make sure that you have created a RAM user named `testuser`.

If you configure the `Principal` element based on the following code, the RAM role can be assumed by the RAM role named `testrole` of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:role/testrole"                
                ]
            }                                 
```

**Note:** Before you edit the trust policy, make sure that you have created a RAM role named `testrole`.

## Example 2: Change the trusted entity of a RAM role to an Alibaba Cloud service

If the `Principal` element in a policy includes the `Service` field, the trusted entity is an **Alibaba Cloud service**. A RAM role to which the policy is attached can be assumed by a trusted Alibaba Cloud service of the current Alibaba Cloud account.

In the following policy, the RAM role can be assumed by the Elastic Compute Service \(ECS\) service of the current Alibaba Cloud account.

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Service": [
                    "ecs.aliyuncs.com"
                ]
            }
        }
    ],
    "Version": "1"
}
```

## Example 3: Change the trusted entity of a RAM role to an IdP

If the `Principal` element includes the `Federated` field, the trusted entity is an **IdP**. The RAM role can be assumed by all users in the IdP.

In the following policy, the RAM role can be assumed by all users in the IdP named `testprovider` of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Principal": {
                "Federated": [
                    "acs:ram::123456789012****:saml-provider/testprovider"
                ]
            },
            "Condition":{
                "StringEquals":{
                    "saml:recipient":"https://signin.alibabacloud.com/saml-role/sso"
                }
            }
        }
    ],
    "Version": "1"
}
```

## Additional considerations

The trusted entity of a policy that is attached to a service-linked role cannot be changed. This is because the policy is defined by the linked service. For more information, see [Service-linked roles](/intl.en-US/RAM Role Management/Service-linked roles.md).

