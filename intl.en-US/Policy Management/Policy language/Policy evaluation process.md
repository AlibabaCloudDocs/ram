# Policy evaluation process

If a RAM identity \(RAM user or role\) initiates a resource access request, a policy evaluation process is performed to determine whether to allow the request. The request can be initialized by using the Alibaba Cloud Management Console, API, or CLI. This topic describes the policy evaluation process of Alibaba Cloud.

## Overview

Alibaba Cloud provides multiple types of policies. A complete policy evaluation process includes the following steps:

1.  Alibaba Cloud gathers all types of policies involved in access requests, including [control policies](), session policies, identity-based policies, and resource-based policies.
2.  Alibaba Cloud evaluates policies in sequence, as shown in the [Basic evaluation process](#section_3zn_he0_r0n). After Alibaba Cloud evaluates a policy, Alibaba Cloud decides whether to evaluate the next policy based on the decision. The evaluation continues until a final decision is obtained.

## Basic evaluation process

All policies are evaluated based on the basic evaluation process, as shown in the following figure.

![Basic evaluation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3097519161/p260631.png)

The basic evaluation process includes the following steps:

1.  Alibaba Cloud first checks whether an applicable policy that apply to a request includes a Deny statement. This is because Deny statements take precedence in policy evaluation.
    -   If an applicable policy includes a Deny statement, the evaluation ends. Explicit Deny is returned.
    -   If an applicable policy does not include a Deny statement, the evaluation continues.
2.  Alibaba Cloud checks whether an applicable policy that apply to a request includes an Allow statement.
    -   If an applicable policy includes an Allow statement, the evaluation ends. Allow is returned.
    -   If an applicable policy does not include an Allow statement, the evaluation ends. Implicit Deny is returned.

The following table describes the possible decisions.

|Decision|Description|
|--------|-----------|
|Allow|If an applicable policy includes an Allow statement rather than a Deny statement, Allow is returned.|
|Explicit Deny|If an applicable policy includes a Deny statement, Explicit Deny is returned. If the applicable policy includes both a Deny statement and an Allow statement, the deny overrides the allow. In this case, Explicit Deny is returned.|
|Implicit Deny|If an applicable policy neither includes an Allow statement nor a Deny statement, Implicit Deny is returned. By default, all the requests initiated by a Resource Access Management \(RAM\) identity are implicitly denied.|

## Standard evaluation process

The following figure shows how policies are evaluated and how a final decision is made.

**Note:** The majority of Alibaba Cloud services are separated based on the accounts. Operations performed for a service take effect only within a single account. Some services, such as Object Storage Service, allow cross-account accesses. However, the policy evaluation process applies to all cases.

![Standard evaluation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3097519161/p260652.png)

A standard evaluation process consists of the following steps:

1.  **Control policy evaluation**

    [Control policies]() allow you to manage the permission boundaries of the folders or member accounts in a resource directory. For example, the resources to be accessed belong to a member account in a [resource directory]() and the Control Policy feature is enabled. Alibaba Cloud evaluates the control policy based on the [Basic evaluation process](#section_3zn_he0_r0n). Otherwise, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
2.  **Session policy evaluation**

    Session policies are policies that you pass as parameters when you programmatically create a temporary session for a RAM role. To programmatically create a role session, call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) API operation. If a RAM role initiates an access request and a session policy is present, Alibaba Cloud evaluates the session policy based on the [Basic evaluation process](#section_3zn_he0_r0n). Otherwise, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
3.  **Identity-based and resource-based policy evaluation**

    Identity-based policies and resource-based policies are evaluated at the same time. Decisions are temporarily saved for combination later.

    -   **Identity-based policy evaluation**

        For a RAM user, identity-based policies include the policies attached to the RAM user and the policies inherited from the group to which the RAM user belongs. For a RAM role, identity-based policies are the policies attached to the RAM role. Identity-based policies are divided into account-class identity-based policies and resource group-class identity-based policies, which have different authorization granularity. Account-class identity-based policies have a higher priority than resource group-class identity-based policies during evaluation.

        The following evaluation process is used to evaluate identity-based policies:

        1.  Alibaba Cloud checks whether the RAM identity that initiates the access request has an account-class identity-based policy.
            -   If an account-class identity-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](#section_3zn_he0_r0n). Alibaba Cloud decides whether to evaluate the next policy based on the decision:
                -   If Explicit Deny or Allow is returned, the evaluation ends. The returned decision is temporarily saved as Decision A.
                -   If Implicit Deny is returned, the evaluation continues.
            -   If an account-class identity-based policy is absent, the evaluation continues.
        2.  Alibaba Cloud checks whether the RAM identity that initiates the access request has a resource group-class identity-based policy.
            -   If a resource group-class identity-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](#section_3zn_he0_r0n). The returned decision is temporarily saved as Decision A.
            -   If a resource group-class identity-based policy is absent, Implicit Deny is saved as Decision A.
    -   **Resource-based policy evaluation**

        Alibaba Cloud checks whether the resources to be accessed have a resource-based policy.

        -   If a resource-based policy is present, Alibaba Cloud evaluates the policy based on the [Basic evaluation process](#section_3zn_he0_r0n). The returned decision is temporarily saved as Decision B.
        -   If a resource-based policy is absent, Implicit Deny is saved as Decision B.
        **Note:** Alibaba Cloud provides bucket policies for Object Storage Service \(OSS\) buckets and trust policies for RAM roles. If the resources to be accessed are neither OSS buckets nor RAM roles, this step is skipped. Instead, the returned decision of identity-based policy is regarded as a final decision.

4.  **Decisions combination**

    Alibaba Cloud combines Decision A and Decision B. The following combination logic is used to combine Decision A and Decision B:

    -   If an explicit deny exists, the final decision is Explicit Deny.
    -   If an allow exists, the final decision is Allow.
    -   If neither an explicit deny nor an allow exists, the final decision is Implicit Deny.
    **Note:**

    -   The combination logic also depends on the cloud service to which the resources to be accessed belong. For information about exceptions, see [Policy evaluation process of assuming a RAM role](/intl.en-US/Policy Management/Policy language/Policy evaluation process of assuming a RAM role.md).
    -   If the resources to be accessed belong to OSS, the bucket access control list \(ACL\) and object ACL are evaluated after policies are evaluated. For more information, see [Authentication](/intl.en-US/Developer Guide/Data security/Access and control/Authentication.md).

If the final decision is Allow, the request is allowed. Whether the final decision is Explicit Deny or Implicit Deny, the request is denied.

