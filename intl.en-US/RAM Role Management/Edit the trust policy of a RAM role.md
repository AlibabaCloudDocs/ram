# Edit the trust policy of a RAM role

This topic describes how to change the trusted entity of a Resource Access Management \(RAM\) role to an Alibaba Cloud account, Alibaba Cloud service, or identity provider \(IdP\). You can change the trusted entity of a RAM role by editing the trust policy that is attached to the RAM role.

When you create a RAM role, you can specify an Alibaba Cloud account, Alibaba Cloud service, or IdP as the trusted entity of the RAM role. In most cases, you do not need to change the trusted entity after you create a RAM role. If you have to change the trusted entity, you can use one of the methods that are described in this topic. After you change the trusted entity, you must test whether the RAM role functions as expected.

## Procedure

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.

2.  In the left-side navigation pane, click **RAM Roles**.

3.  On the **RAM Roles** page, click the name of the RAM role in the **RAM Role Name** column.

4.  On the page that appears, click the **Trust Policy Management** tab. On this tab, click **Edit Trust Policy**.

5.  In the **Edit Trust Policy** pane, click **OK**.


## Change the trusted entity of a RAM role to an Alibaba Cloud account

If the `Principal` element in a policy contains the `RAM` field, it indicates that the trusted entity is an **Alibaba Cloud account**. A RAM role to which the policy is attached can be assumed by authorized RAM users of the trusted Alibaba Cloud account.

For example, the following policy indicates that the RAM role can be assumed by all RAM users of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

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

If you set the `Principal` element to the following value, the RAM role can be assumed only by the RAM user named `testuser` of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:user/testuser"
                ]
            }                   
```

**Note:** Before you edit the trust policy, make sure that you have created a RAM user named `testuser`.

If you set the `Principal` element to the following value, the RAM role can be assumed only by the RAM role named `testrole` of the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

```
            "Principal": {
                "RAM": [
                    "acs:ram::123456789012****:role/testrole"                
                ]
            }                                 
```

**Note:** Before you edit the trust policy, make sure that you have created a RAM role named `testrole`.

## Change the trusted entity of a RAM role to an Alibaba Cloud service

If the `Principal` element in a policy contains the `Service` field, it indicates that the trusted entity is an **Alibaba Cloud service**. A RAM role to which the policy is attached can be assumed by a trusted Alibaba Cloud service of the current Alibaba Cloud account.

For example, the following trust policy indicates that the RAM role can be assumed by the Elastic Compute Service \(ECS\) service of the current Alibaba Cloud account.

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

## Change the trusted entity of a RAM role to an IdP

If the `Principal` element contains the `Federated` field, it indicates that the trusted entity is an **IdP**. A RAM role to which the policy is attached can be assumed by all users in the IdP.

For example, the following policy indicates that the RAM role can be assumed by all users in the IdP named `testprovider`. The IdP is configured under the Alibaba Cloud account whose ID is 123456789012\*\*\*\*.

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

The trusted entity of a policy that is attached to a service linked role cannot be changed. This is because the policy is predefined by the linked service. For more information about service linked roles, see [Service linked roles](/intl.en-US/RAM Role Management/Service linked roles.md).

