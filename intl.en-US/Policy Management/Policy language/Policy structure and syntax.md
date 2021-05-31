# Policy structure and syntax

This topic describes the structure and syntax that are used to create or update policies in Resource Access Management \(RAM\).

## Conventions for policy syntax

The following conventions are used for the policy syntax:

-   Characters in a policy
    -   The following characters are reserved JSON characters in the policy syntax: `{ } [ ] " , :`.
    -   The following characters are special characters in the policy syntax: `= < > ( ) |`.
-   Use of characters
    -   If an element can have more than one value, you can perform one of the following operations:
        -   Use a comma \(,\) as the delimiter to separate each value and an ellipsis \(...\)to describe the remaining values.

            Example: `[ <action_string>, <action_string>, ...]`.

        -   Include only one value.

            Example: `"Action": [<action_string>]` and `"Action": <action_string>`.

    -   A question mark \(?\) that follows an elementindicates that the element is optional.

        Example: `<condition_block?>`.

    -   A vertical bar \(\|\) between elements indicates multiple options. Only one of the options can be used.

        Example: `("Allow" | "Deny")`.

    -   Strings are enclosed in double quotation marks \("\).

        Example: `<version_block> = "Version" : ("1")`.


## Policy structure

The policy structure includes the following components:

-   The version number.
-   A list of statements. Each statement contains the following elements: effect, action, resource, and condition. The condition element is optional.

![Policy structure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4888549951/p14403.png)

## Policy syntax

```
policy  = {
     <version_block>,
     <statement_block>
}
<version_block> = "Version" : ("1")
<statement_block> = "Statement" : [ <statement>, <statement>, ... ]
<statement> = { 
    <effect_block>,
    <action_block>,
    <resource_block>,
    <condition_block?>
}
<effect_block> = "Effect" : ("Allow" | "Deny")  
<action_block> = "Action" : 
    ("*" | [<action_string>, <action_string>, ...])
<resource_block> = "Resource" : 
    ("*" | [<resource_string>, <resource_string>, ...])
<condition_block> = "Condition" : <condition_map>
<condition_map> = {
  <condition_type_string> : { 
      <condition_key_string> : <condition_value_list>,
      <condition_key_string> : <condition_value_list>,
      ...
  },
  <condition_type_string> : {
      <condition_key_string> : <condition_value_list>,
      <condition_key_string> : <condition_value_list>,
      ...
  }, ...
}  
<condition_value_list> = [<condition_value>, <condition_value>, ...]
<condition_value> = ("String" | "Number" | "Boolean" | "Date and time" | "IP address")
```

The following list describes the policy syntax:

-   Version: The current policy version is 1. The version cannot be changed.
-   Statements: A policy can have multiple statements.
    -   The effect of each statement can be either `Allow` or `Deny`.

        **Note:** In a statement, both the Action and Resource elements can have multiple values.

    -   Each statement can have its own conditions.

        **Note:** A condition block can contain multiple conditions that have different operators.

-   Permission precedence: You can attach multiple policies to a RAM user. If policies that apply to a request include an `Allow` statement and a `Deny` statement, the Deny statement takes precedence over the Allow statement.
-   Element value:
    -   If an element value is a sting, number, date, time, Boolean value, or an IP address, the value must be enclosed in double quotation marks \("\).
    -   If an element value is a string, wildcard characters such as asterisks \(`*`\) and question marks \(`?`\)can be used.
        -   An asterisk \(`*`\) indicates the number \(which includes zero\) of letters that you can use. For example, if the element value is `ecs:Describe*`, you can use all Elastic Compute Service \(ECS\) operations that start with `Describe`.
        -   A question mark \(`?`\)indicates an allowed letter.

## Policy syntax check

Policies are stored as JSON files. When you create or update a policy, RAM checks whether the JSON syntax is valid before the policy can be created or updated. You can also use tools such as JSON validators and editors to check whether policies meet JSON syntax standards. For more information about JSON syntax standards, see [RFC 7159](http://tools.ietf.org/html/rfc7159).

**Related topics**  


[Policy elements](/intl.en-US/Policy Management/Policy language/Policy elements.md)

[Overview of sample policies]()

