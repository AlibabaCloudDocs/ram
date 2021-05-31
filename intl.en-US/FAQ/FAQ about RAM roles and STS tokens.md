# FAQ about RAM roles and STS tokens

This topic provides answers to some frequently asked questions about Resource Access Management \(RAM\) roles and Security Token Service \(STS\) tokens.

## What are the types of RAM roles?

RAM roles are classified into the following types based on the trusted entity:

-   **Alibaba Cloud account**
-   **Alibaba Cloud service**
-   **Identity provider \(IdP\)**

## What entities can assume the three types of RAM role?

-   **Alibaba Cloud account**: RAM users of a trusted Alibaba Cloud account can assume this type of RAM role. RAM users that assume this type of RAM role can belong to their Alibaba Cloud accounts or other Alibaba Cloud accounts. This type of RAM role is used for cross-account access and temporary authorization.
-   **Alibaba Cloud service**: Alibaba Cloud services can assume this type of RAM role. RAM roles that Elastic Compute Service \(ECS\) instances assume are categorized into this type of RAM role. In this case, the trusted entity is ECS. For more information, see [Use RAM roles to access other Alibaba Cloud services](/intl.en-US/Best Practices/Use RAM roles to access other Alibaba Cloud services.md). The roles of this type are used to grant the permissions to manage your resources. The permissions are granted to Alibaba Cloud services.
-   **IdP**: Users of a trusted IdP can assume this type of RAM role. The roles of this type are used to implement single sign-on \(SSO\) between Alibaba Cloud and a trusted IdP.

## Can I specify the RAM role that a RAM user can assume?

Yes, you can specify the RAM role that a RAM user can assume. You can create a custom policy to specify the RAM role that a RAM user can assume. The following sample code gives an example of a custom policy:

```
{
    "Statement": [
        {
            "Action": "sts:AssumeRole",
            "Effect": "Allow",
            "Resource": "acs:ram:*:$accountId:role/$roleName"
        }
    ],
    "Version": "1"
}
```

**Note:**

-   In this policy, the `Resource` element specifies the Alibaba Cloud Resource Name \(ARN\) of the RAM role. For more information about how to find the ARN of a RAM role, see [How do I find the ARN of the RAM role?](#section_qbw_mhy_173). In this element, `$accountId` specifies the ID of the Alibaba Cloud account and `$roleName` specifies the name of the RAM role.
-   You can attach this policy to the RAM user to specify the RAM role that a RAM user can assume. For more information about how to attach a policy to a RAM user, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Authorization management/Grant permissions to a RAM user.md).

## How do I find the ARN of a RAM role?

1.  To find the ARN of a RAM role, log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click **RAM Roles**.
3.  On the RAM Roles page, click the name of the RAM role.
4.  In the **Basic Information** section, view the ARN of the RAM role.

    ![ ARN of a RAM role](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2801914951/p60601.png)


## Why does an error occur when a RAM user accesses STS?

When a RAM user uses the API, a CLI, or an SDK to call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation, the following error message may be returned:

```
Error message: You are not authorized to do this action. You should be authorized by RAM.
```

The error message is returned due to the following causes:

-   The required policies are not granted to the RAM user. To resolve this issue, attach the AliyunSTSAssumeRoleAccess policy or a custom policy to the RAM user. For more information, see [Can I specify the RAM role that a RAM user can assume?](#section_c5c_e3t_at9)
-   The RAM user is not authorized to assume the RAM role. To resolve this issue, add the RAM user to the Principal element in the trust policy of the RAM role. For more information, see [Edit the trust policy of a RAM role](/intl.en-US/RAM Role Management/Edit the trust policy of a RAM role.md).

## Is the number of STS API requests limited?

Yes, the number of STS API requests is limited. The AssumeRole operation can be called up to 100 times per second for each Alibaba Cloud account. API requests that are sent by using RAM users and RAM roles within the Alibaba Cloud account are also counted. If the number of API requests exceeds 100, the following error message is returned:

```
Request was denied due to user flow control
```

## What are the permissions of an STS token?

The permissions of an STS token are the permissions of a specific RAM role that are specified by the `Policy` parameter when you call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation.

**Note:** If you do not specify the Policy parameter when you call the AssumeRole operation, the returned STS token has all the permissions of the specific RAM role.

## What is the validity period of an STS token?

The validity period of an STS token ranges from 900 seconds to the maximum session duration that you specify. The default validity period is 3,600 seconds.

**Note:**

-   You can specify the DurationSeconds parameter when you call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation to specify the validity period of an STS token.
-   You can use the RAM console or API to configure the maximum session duration of a RAM role. For more information, see [Set the maximum session duration for a RAM role](/intl.en-US/RAM Role Management/Set the maximum session duration for a RAM role.md).

## If multiple STS tokens were obtained at different points in time, are the old and new tokens valid at the same time?

Yes, the old and new tokens are valid at the same time. All STS tokens are valid before their expiration time.

## What do I do if STS tokens are disclosed?

If the STS tokens that are obtained after a RAM user assumes a RAM role are disclosed, perform the following steps to disable the STS tokens:

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) by using your Alibaba Cloud account.
2.  Detach all policies from the RAM role.

    For more information, see [Remove permissions from a RAM role](/intl.en-US/RAM Role Management/Remove permissions from a RAM role.md).

3.  Delete the RAM role.

    For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

    After the RAM role is deleted, the STS tokens that are not expired become invalid.


If you want to continue using the deleted RAM role, create a RAM role that has the same name and attach the same policies to the new RAM role.

