# Policy evaluation process of assuming a RAM role

If a trusted entity attempts to assume a RAM role, a policy evaluation process is performed to determine whether to allow the request. The request can be initialized by using the Alibaba Cloud Management Console, API, or CLI. This topic describes the policy evaluation process that applies when you assume a Resource Access Management \(RAM\) role.

**Note:** The policy evaluation process of assuming a RAM role is the same as the [Policy evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.md) except the decision combination process. If you are familiar with the [Policy evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.md), you only need to read the Decisions combination section of this topic.

If you create a role, you must specify a [trusted entity](/intl.en-US/RAM Role Management/RAM role overview.md) for the role by adding a trust policy. In this case, trust policies take effect based on resources. If a trusted entity assumes a RAM role, the trusted entity must be granted required permissions. In this case, trust policies take effect based on identities.

When a trusted entity assumes a RAM role, the role is a resource to be accessed. Alibaba Cloud evaluates policies in sequence, as shown in the following figure.

![Policy evaluation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4297519161/p261793.png)

Alibaba Cloud evaluates multiple types of policies involved in the request based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). A policy evaluation process consists of the following steps:

1.  **Control policy evaluation**

    [Control policies]() allow you to manage the permission boundaries of the folders or member accounts in a resource directory. For example, the RAM role to be assumed belongs to a member account in a [resource directory]() and the Control Policy feature is enabled. Alibaba Cloud evaluates the control policy based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). Otherwise, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
2.  **Session policy evaluation**

    Session policies are policies that you pass as parameters when you programmatically create a temporary session for a RAM role. To programmatically create a role session, call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) API operation. If a RAM role initiates an access request and a session policy is present, Alibaba Cloud evaluates the session policy based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). Otherwise, this step is skipped.

    **Note:** If you implement role-based single sign-on \(SSO\), a session policy is absent. Therefore, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
3.  **Identity-based and resource-based policy evaluation**

    Identity-based policies and resource-based policies are evaluated at the same time. Decisions are temporarily saved for combination later.

    -   **Identity-based policy evaluation**

        For a RAM user, identity-based policies include the policies attached to the RAM user and the policies inherited from the group to which the RAM user belongs. For a RAM role, identity-based policies are the policies attached to the RAM role. Identity-based policies are divided into account-class identity-based policies and resource group-class identity-based policies, which have different authorization granularity. Account-class identity-based policies have a higher priority than resource group-class identity-based policies during evaluation.

        **Note:** If you implement role-based SSO, the logon is not complete and an identity-based policy is absent. Therefore, this step is skipped. The returned decision of the resource-based policy is regarded as a final decision.

        The following evaluation process is used to evaluate identity-based policies:

        1.  Alibaba Cloud checks whether the RAM identity that initiates the access request has an account-class identity-based policy.
            -   If an account-class identity-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). Alibaba Cloud decides whether to evaluate the next policy based on the decision:
                -   If Explicit Deny or Allow is returned, the evaluation ends. The returned decision is temporarily saved as Decision A.
                -   If Implicit Deny is returned, the evaluation continues.
            -   If an account-class identity-based policy is absent, the evaluation continues.
        2.  Alibaba Cloud checks whether the RAM identity that initiates the access request has a resource group-class identity-based policy.
            -   If a resource group-class identity-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). The returned decision is temporarily saved as Decision A.
            -   If a resource group-class identity-based policy is absent, Implicit Deny is saved as Decision A.
    -   **Resource-based policy evaluation**

        Alibaba Cloud checks whether the RAM role to be assumed has a trust policy.

        -   If a resource-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.mdsection_3zn_he0_r0n). The returned decision is temporarily saved as Decision B.
        -   If a resource-based policy is absent, Implicit Deny is saved as Decision B.
4.  **Decisions combination**

    Alibaba Cloud combines Decision A and Decision B. The combination logic is different from that of the standard [Policy evaluation process](/intl.en-US/Policy Management/Policy language/Policy evaluation process.md). Only when Decision A and Decision B are both allowed, the request to assume a RAM role is allowed.

    The following combination logic is used to combine Decision A and Decision B:

    -   If an explicit deny exists, the final decision is Explicit Deny.
    -   If Decision A and Decision B are both allowed, the final decision is Allow. The evaluation ends.
    -   In addition to the preceding two cases, the final decision is Implicit Deny. The evaluation ends.

