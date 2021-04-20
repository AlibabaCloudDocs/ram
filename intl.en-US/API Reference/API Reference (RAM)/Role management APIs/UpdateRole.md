# UpdateRole

Changes the description of a RAM role.

This topic provides an example to show how to change the description of ECSAdmin to ECS administrator.

## Debugging

OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer.OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateRole|The operation that you want to perform. Set the value to UpdateRole. |
|RoleName|String|Yes|ECSAdmin|The name of the RAM role.

The name must be 1 to 64 characters in length and can contain letters, digits, periods \(.\),and hyphens \(-\). |
|NewAssumeRolePolicyDocument|String|No|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::12345678901234\*\*\*\*:root" \} \} \], "Version": "1" \}|The policy that specifies the trusted entity to assume the RAM role. |
|NewMaxSessionDuration|Long|No|3600|The maximum session duration of the RAM role.

Valid values: 3600 to 43200. Unit: seconds.Default value: 3600.

If you do not specify this parameter, the default value is used. |
|NewDescription|String|No|ECS administrator|The new description of the RAM role.

The value must be 1 to 1,024 characters in length. |

For more information about common parameters, see Common parameters.

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |
|Role|Struct| |The information of the RAM role. |
|Arn|String|acs:ram::123456789012\*\*\*\*:role/ECSAdmin|The Alibaba Cloud Resource Name \(ARN\) of the role. |
|AssumeRolePolicyDocument|String|\{ "Statement": \[ \{ "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": \{ "RAM": "acs:ram::123456789012\*\*\*\*:root" \} \} \], "Version": "1" \}|The policy that specifies the trusted entity to assume the RAM role. |
|CreateDate|String|2015-01-23T12:33:18Z|The time when the RAM role was created. |
|Description|String|ECS administrator|The description of the RAM role. |
|MaxSessionDuration|Long|3600|The maximum session duration of the RAM role. |
|RoleId|String|901234567890\*\*\*\*|The ID of the RAM role. |
|RoleName|String|ECSAdmin|The name of the RAM role. |
|UpdateDate|String|2015-01-23T12:33:18Z|The time when the description of the RAM role was changed. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=UpdateRole
&RoleName=ECSAdmin
&Description=ECS administrator
&<Common request parameters>
```

Sample success responses

XML format

```
<UpdateRoleResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <Role>
            <RoleId>901234567890****</RoleId>
            <RoleName>ECSAdmin</RoleName>
            <Arn>acs:ram::123456789012****:role/ECSAdmin</Arn>
            <Description>ECS administrator</Description>
            <MaxSessionDuration>3600</MaxSessionDuration>
            <AssumeRolePolicyDocument>{ "Statement": [ { "Action": "sts:AssumeRole", "Effect": "Allow", "Principal": { "RAM": "acs:ram::123456789012****:root" } } ], "Version": "1" }</AssumeRolePolicyDocument>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
            <UpdateDate>2015-01-23T12:33:18Z</UpdateDate>
      </Role>
</UpdateRoleResponse>
```

JSON format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "Role": {
        "RoleId": "901234567890****",
        "RoleName": "ECSAdmin",
        "Arn": "acs:ram::123456789012****:role/ECSAdmin",
        "Description": "ECS administrator",
        "MaxSessionDuration": 3600,
        "AssumeRolePolicyDocument": "{ \"Statement\": [ { \"Action\": \"sts:AssumeRole\", \"Effect\": \"Allow\", \"Principal\": { \"RAM\": \"acs:ram::123456789012****:root\" } } ], \"Version\": \"1\" }",
        "CreateDate": "2015-01-23T12:33:18Z",
        "UpdateDate": "2015-01-23T12:33:18Z"
    }
}
```

## Error codes

For a list of error codes, visit the API Error Center.

