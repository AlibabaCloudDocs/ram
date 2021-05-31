# Policy evaluation process

If a Resource Access Management \(RAM\) identity initiates a resource access request, a policy evaluation process is performed to determine whether to allow the request. The RAM identity is a RAM user or RAM role. The request can be initialized by using the Alibaba Cloud Management Console, API, or a CLI. This topic describes the policy evaluation process of Alibaba Cloud.

## Overview

Alibaba Cloud provides multiple types of policies. A complete policy evaluation process includes the following steps:

1.  Alibaba Cloud collects all types of policies that are involved in the access request. The policies include [control policies](), session policies, identity-based policies, and resource-based policies.
2.  Alibaba Cloud evaluates policies in sequence. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. After Alibaba Cloud evaluates a policy, Alibaba Cloud decides whether to evaluate the next policy based on the decision. The evaluation continues until a final decision is obtained.

## Basic evaluation process

All types of policies are evaluated based on the basic evaluation process, as shown in the following figure.

![Basic evaluation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3097519161/p260631.png)

The basic evaluation process includes the following steps:

1.  Alibaba Cloud first checks whether a policy that is involved in a request includes a Deny statement. This is because Deny statements take precedence over Allow statements in policy evaluation.
    -   If the policy includes a Deny statement, the evaluation ends. Explicit Deny is returned.
    -   If the policy does not include a Deny statement, the evaluation continues.
2.  Alibaba Cloud checks whether the policy includes an Allow statement.
    -   If the policy includes an Allow statement, the evaluation ends. Allow is returned.
    -   If the policy does not include an Allow statement, the evaluation ends. Implicit Deny is returned.

The following table describes the possible decisions.

|Decision|Description|
|--------|-----------|
|Allow|If a policy includes an Allow statement instead of a Deny statement, Allow is returned.|
|Explicit Deny|If a policy includes a Deny statement, Explicit Deny is returned. If the policy includes both a Deny statement and an Allow statement, the Deny statement takes precedence over the Allow statement. In this case, Explicit Deny is returned.|
|Implicit Deny|If a policy does not include an Allow statement or a Deny statement, Implicit Deny is returned. By default, all the requests initiated by a RAM identity are implicitly denied.|

## Standard evaluation process

The following figure shows how policies are evaluated and how a final decision is made.

**Note:** The majority of Alibaba Cloud services are separated based on Alibaba Cloud accounts. Some services allow access within the same account. Some services, such as Object Storage Service \(OSS\), allow access across accounts. The policy evaluation process applies to all cases.

![Standard evaluation process](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3097519161/p260652.png)

A standard evaluation process includes the following steps:

1.  **Control policy evaluation**

    [Control policies]() allow you to manage the permission boundaries of the member accounts in a resource directory. If you want to access the resources of a member account in a [resource directory]() and a control policy exists, Alibaba Cloud evaluates the control policy based on the basic evaluation process. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. Otherwise, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
2.  **Session policy evaluation**

    Session policies are policies that you pass as parameters when you programmatically create a temporary session for a RAM role. To programmatically create a role session, call the [AssumeRole](/intl.en-US/API Reference/API Reference (STS)/Operation interfaces/AssumeRole.md) operation. If a RAM role initiates an access request and a session policy exists, Alibaba Cloud evaluates the session policy based on the basic evaluation process. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. Otherwise, this step is skipped.

    Alibaba Cloud decides whether to evaluate the next policy based on the decision:

    -   If Explicit Deny or Implicit Deny is returned, the evaluation ends. The returned decision is the final decision.
    -   If Allow is returned, the evaluation continues.
3.  **Identity-based and resource-based policy evaluation**

    Identity-based policies and resource-based policies are evaluated at the same time. Decisions are temporarily saved and then combined at a later time.

    -   **Identity-based policy evaluation**

        For a RAM user, identity-based policies include the policies attached to the RAM usage and the policies inherited from the group to which the RAM user belongs. For a RAM role, identity-based policies are the policies attached to the RAM role. Identity-based policies are classified into account-class identity-based policies and resource group-class identity-based policies. The two classifications have different authorization granularities. During evaluation, account-class identity-based policies have a higher priority than resource group-class identity-based policies.

        The following evaluation process is used to evaluate identity-based policies:

        1.  Alibaba Cloud checks whether the RAM identity that initiates the access request has an account-class identity-based policy.
            -   If an account-class identity-based policy exists, Alibaba Cloud evaluates the policy based on the basic evaluation process. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. Alibaba Cloud decides whether to evaluate the next policy based on the decision:
                -   If Explicit Deny or Allow is returned, the evaluation ends. The returned decision is temporarily saved as Decision A.
                -   If Implicit Deny is returned, the evaluation continues.
            -   If no account-class identity-based policies exist, the evaluation continues.
        2.  Alibaba Cloud checks whether the RAM identity that initiates the access request has a resource group-class identity-based policy.
            -   If a resource group-class identity-based policy exists, Alibaba Cloud evaluates the policy based on the basic evaluation process. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. The returned decision is temporarily saved as Decision A.
            -   If no resource group-class identity-based policies exist, Implicit Deny is saved as Decision A.
    -   **Resource-based policy evaluation**

        Alibaba Cloud checks whether the resources to be accessed have a resource-based policy.

        -   If a resource-based policy exists, Alibaba Cloud evaluates the policy based on the basic evaluation process. For more information, see the "[Basic evaluation process](#section_3zn_he0_r0n)" section of this topic. The returned decision is temporarily saved as Decision B.
        -   If no resource-based policies exist, Implicit Deny is saved as Decision B.
        **Note:** Alibaba Cloud provides bucket policies for OSS buckets and trust policies for RAM roles. If the resources to be accessed are not OSS buckets or RAM roles, this step is skipped. The returned decision of the identity-based policy is considered as the final decision.

4.  **Combination of decisions**

    Alibaba Cloud combines Decision A and Decision B. The following logic is used to combine the decisions:

    -   If an Explicit Deny decision is returned, the final decision is Explicit Deny. The evaluation ends.
    -   If an Allow decision is returned, the final decision is Allow. The evaluation ends.
    -   If neither an Explicit Deny nor an Allow decision is returned, the final decision is Implicit Deny. The evaluation ends.
    **Note:**

    -   Except for the preceding logic, the combination logic also depends on the cloud service to which the resources to be accessed belong. For information about exceptions, see [Policy evaluation process of assuming a RAM role](/intl.en-US/Policy Management/Policy language/Policy evaluation process of assuming a RAM role.md).
    -   If the resources to be accessed belong to OSS, the bucket access control list \(ACL\) or object ACL are evaluated after policies are evaluated. For more information, see [Authentication](/intl.en-US/Developer Guide/Data security/Access and control/Authentication.md).

If the final decision is Allow, the request is allowed. If the final decision is Explicit Deny or Implicit Deny, the request is denied.

