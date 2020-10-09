# FAQ about RAM roles and STS tokens

This topic provides answers to some commonly asked questions about Resource Access Management \(RAM\) roles and Security Token Service \(STS\) tokens.

## How are RAM roles classified?

RAM roles are classified into the following types based on trusted entities:

-   **Alibaba Cloud account**
-   **Alibaba Cloud service**
-   **Identity provider \(IdP\)**

## What entities can assume the three types of RAM roles?

-   **Alibaba Cloud account**: RAM users under an Alibaba Cloud account can assume this type of RAM role. RAM users who assume this type of RAM role can belong to their parent Alibaba Cloud accounts or other Alibaba Cloud accounts. This type of RAM role is used for cross-account access and temporary authorization.
-   **Alibaba Cloud service**: Alibaba Cloud services can assume this type of RAM role. For example, an ECS instance can assume a RAM role of this type. The trusted entity of the RAM role is the ECS service. For more information, see [Use RAM roles to access other Alibaba Cloud services](/intl.en-US/Best Practices/Use RAM roles to access other Alibaba Cloud services.md). The RAM roles of this type are used for granting Alibaba Cloud services the required permissions to manage your resources.
-   **IdP**: Users of a trusted IdP can assume this type of RAM role. The RAM roles of this type are used to implement single sign-on \(SSO\) between Alibaba Cloud and a trusted IdP.

## Can I specify the RAM role that a RAM user can assume?

Yes, you can create a custom policy to specify the RAM role that a RAM user can assume. The following sample code gives an example of a custom policy:

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

-   In this policy, the `Resource` element indicates the Alibaba Cloud Resource Name \(ARN\) of the RAM role. For more information about how to find the ARN of a RAM role, see [How do I find the ARN of the RAM role?](#section_qbw_mhy_173) In this element, `$accountId` indicates the ID of the Alibaba Cloud account and `$roleName` indicates the name of the RAM role.
-   The preceding policy specifies the RAM role that a RAM user can assume. For more information about how to attach the policy to the RAM user, see [Grant permissions to a RAM user](/intl.en-US/RAM User Management/Grant permissions to a RAM user.md).

## How do I find the ARN of a RAM role?

1.  To find the ARN of a RAM role, log on to the [RAM console](https://ram.console.aliyun.com/).
2.  In the left-side navigation pane, click RAM Roles. On the **RAM Roles** page, click the name of the RAM role.
3.  In the **Basic Information** section, view the ARN of the RAM role.

    ![ ARN of a RAM role](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/2801914951/p60601.png)


## Why does an error occur when a RAM user accesses STS?

When a RAM user uses the API, CLI, or SDK to call the [AssumeRole](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md) operation, the following error message may be returned:

```
Error message: You are not authorized to do this action. You should be authorized by RAM.
```

The error message is returned due to the following causes:

-   The required permissions are not granted to the RAM user. To resolve this issue, grant the RAM user the required permissions by attaching the AliyunSTSAssumeRoleAccess policy or a custom policy to the RAM user. For more information, see [Can I specify the RAM role that a RAM user can assume?](#section_c5c_e3t_at9)
-   The RAM user is not authorized to assume the RAM role. To resolve this issue, add the RAM user to the Principal element in the trust policy of the RAM role. For more information, see [Edit the trust policy of a RAM role](/intl.en-US/RAM Role Management/Change the trusted entity of a RAM role.md).

## Is the number of STS API requests limited?

Yes, STS supports up to 100 AssumeRole API requests per second for each Alibaba Cloud account. API requests that are sent by using RAM users and RAM roles under the Alibaba Cloud account are also counted. If the number of API requests reaches 100, the following error message is returned:

```
Request was denied due to user flow control
```

## What are the permissions of an STS token?

The permissions of an STS token are the specified RAM role's permissions in the policy that is specified by the `Policy` parameter when the [AssumeRole](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md) API operation is called.

**Note:** If you do not specify the Policy parameter when calling the AssumeRole API operation, the returned STS token has all the permissions of the specified RAM role.

## What is the validity period of an STS token?

The validity period of an STS token ranges from 900 seconds to the maximum session duration that you specify. The default validity period is 3,600 seconds.

**Note:**

-   You can specify the DurationSeconds parameter when you call the [AssumeRole](/intl.en-US/API Reference (STS)/Operation interfaces/AssumeRole.md) API operation to set the validity period of an STS token.
-   You can use the console or API to set the maximum session duration of a RAM role. For more information, see [Set the maximum session duration for a RAM role](/intl.en-US/RAM Role Management/Set the maximum session duration for a RAM role.md).

## If multiple STS tokens have been obtained at different times, are the old and new tokens valid at the same time?

All STS tokens are valid before their expiration time.

## What can I do if STS tokens are disclosed?

If STS tokens that RAM users obtain after assuming a RAM role are disclosed, perform the following steps to disable all of the STS tokens:

1.  Log on to the [RAM console](https://ram.console.aliyun.com/) with an Alibaba Cloud account.
2.  Detach all policies from the RAM role. For more information, see [Remove permissions from a RAM role](/intl.en-US/RAM Role Management/Remove permissions from a RAM role.md).
3.  Delete the RAM role. For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

    After the RAM role is deleted, all of the STS tokens that are obtained by assuming the RAM role and have not expired become invalid.


If you want to continue using the deleted RAM role, create a RAM role with the same name and grant the same permissions to the new RAM role.

