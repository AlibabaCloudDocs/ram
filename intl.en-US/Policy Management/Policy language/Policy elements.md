# Policy elements

This topic describes the elements of policies that are used to define permissions in Alibaba Cloud Resource Access Management \(RAM\).

## Elements

|Element|Description|
|:------|:----------|
|Effect|Specifies whether the statement results in an explicit allow or an explicit deny. Valid values: Allow and Deny.|
|Action|Describes one or more operations that are allowed or denied.|
|Resource|Specifies one or more objects that the statement covers.|
|Condition|Specifies the conditions that are required for a policy to take effect.|

## Rules for using policy elements

-   Effect

    Valid values are Allow and Deny.

    **Note:** If policies that apply to a request include an Allow statement and a Deny statement, the Deny statement takes precedence over the Allow statement.

    Example: `"Effect": "Allow"`

-   Action

    This element can contain one or more values. Valid values are the names of API operations from Alibaba Cloud services.

    **Note:** In most cases, each Alibaba Cloud service has its own set of API operations. For more information, see [Alibaba Cloud services that support RAM](/intl.en-US/Product Introduction/Alibaba Cloud services that support RAM.md).

    Syntax: `<service-name>:<action-name>`.

    -   `service-name`: the name of an Alibaba Cloud service.
    -   `action-name`: one or more API operation names from the service.
    Example: `"Action": ["oss:ListBuckets", "ecs:Describe*", "rds:Describe*"]`

-   Resource

    This element specifies one or more objects that the statement covers.

    Syntax: `acs:<service-name>:<region>:<account-id>:<relative-id>`. The syntax is the same as the format of an Alibaba Cloud Resource Name \(ARN\).

    -   `acs`: the abbreviation of Alibaba Cloud Service, which indicates the public cloud of Alibaba Cloud.
    -   `service-name`: the name of an Alibaba Cloud service.
    -   `region`: the region information. You can use an asterisk \(`*`\) wildcard character to specify all the regions.
    -   `account-id`: the Alibaba Cloud account ID, for example, `123456789012****`. If no ID is required or available, use an asterisk \(`*`\).
    -   `relative-id`: the identifier of the service-related resource. The meaning of this element varies by service. The value of the relative-id element can be a file path. For example, `relative-id = "mybucket/dir1/object1.jpg"` indicates an OSS object.
    Example: `"Resource": ["acs:ecs:*:*:instance/inst-001", "acs:ecs:*:*:instance/inst-002", "acs:oss:*:*:mybucket", "acs:oss:*:*:mybucket/*"]`

-   Condition

    A condition block can contain one or more conditions, and each condition consists of a condition operator, key, and value.

    ![Condition block](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7747714951/p38714.png)

    Evaluation logic:

    -   You can specify one or more values for a condition key. If the value in a request matches any of the values, the condition is met.
    -   You can specify one or more condition keys for a single condition operator in a condition. The condition is met only if all the requirements for the keys are met.
    -   A condition block is met only if all of its conditions are met.
    Condition operators:

    The condition operators are grouped into the following categories: string, number, date and time, Boolean, and IP address.

    |Category|Condition operator|
    |:-------|:-----------------|
    |String|    -   StringEquals
    -   StringNotEquals
    -   StringEqualsIgnoreCase
    -   StringNotEqualsIgnoreCase
    -   StringLike
    -   StringNotLike |
    |Number|    -   NumericEquals
    -   NumericNotEquals
    -   NumericLessThan
    -   NumericLessThanEquals
    -   NumericGreaterThan
    -   NumericGreaterThanEquals |
    |Date and time|    -   DateEquals
    -   DateNotEquals
    -   DateLessThan
    -   DateLessThanEquals
    -   DateGreaterThan
    -   DateGreaterThanEquals |
    |Boolean|Bool|
    |IP address|    -   IpAddress
    -   NotIpAddress |

    Condition keys:

    -   The syntax of a common condition key is `acs:<condition-key>`.

        |Common condition key|Category|Description|
        |:-------------------|:-------|:----------|
        |`acs:CurrentTime`|Date and time|The time when the web server receives a request. Specify the time in the ISO 8601 standard, for example, `2012-11-11T23:59:59Z`.|
        |`acs:SecureTransport`|Boolean|Specifies whether a secure channel is used to send a request. For example, a request can be sent over HTTPS.|
        |`acs:SourceIp`|IP address|The IP address of the client that sends a request. **Note:** If you specify only one value for the `acs:SourceIp` key, the value must be an IP address, for example, 10.0.0.1. CIDR blocks, such as 10.0.0.1/32, cannot be used. |
        |`acs:MFAPresent`|Boolean|Specifies whether multi-factor authentication \(MFA\) is used during user logon.|

    -   The syntax of a condition key that is specific to an Alibaba Cloud service is `<service-name>:<condition-key>`.

        |Condition key specific to an Alibaba Cloud service|Alibaba Cloud service|Category|Description|
        |:-------------------------------------------------|---------------------|:-------|:----------|
        |`ecs:tag/<tag-key>`|ECS|String|The tag key of ECS resources. This key can be customized.|
        |`rds:ResourceTag/<tag-key>`|RDS|String|The tag key of RDS resources. This key can be customized.|
        |`oss:Delimiter`|OSS|String|The delimiter that is used to categorize object names.|
        |`oss:Prefix`|OSS|String|The prefix of object names.|


**Related topics**  


[Policy structure and syntax](/intl.en-US/Policy Management/Policy language/Policy structure and syntax.md)

