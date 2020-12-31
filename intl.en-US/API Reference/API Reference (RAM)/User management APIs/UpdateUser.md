# UpdateUser

Modifies a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer automatically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ram&api=UpdateUser&type=RPC&version=2015-05-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateUser|The operation that you want to perform. Set the value to UpdateUser. |
|UserName|String|Yes|zhangq\*\*\*\*|The name of the RAM user. |
|NewUserName|String|No|xiaoq\*\*\*\*|The name of the new RAM user.

 The name must be 1 to 64 characters in length, and can contain letters, digits, periods \(.\), hyphens \(-\), and underscores \(\_\). |
|NewMobilePhone|String|No|86-1860000\*\*\*\*|The new mobile phone number of the RAM user.

 Format: <International area code\>-<Mobile phone number\> |
|NewDisplayName|String|No|xiaoq\*\*\*\*|The new display name of the RAM user.

 The name must be 1 to 128 characters in length, and can contain letters, digits, periods \(.\), at signs \(@\), hyphens \(-\), and spaces. |
|NewEmail|String|No|xiaoq\*\*\*\*@example.com|The new email address of the RAM user. |
|NewComments|String|No|This is a cloud computing engineer.|The new description.

 The description must be 1 to 128 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |
|User|Struct| |The information about the RAM user. |
|Comments|String|This is a cloud computing engineer.|The description of the RAM user. |
|CreateDate|String|2015-01-23T12:33:18Z|The time when the RAM user was created. |
|DisplayName|String|xiaoq\*\*\*\*|The display name of the RAM user. |
|Email|String|xiaoq\*\*\*\*@example.com|The email address of the RAM user. |
|MobilePhone|String|86-1860000\*\*\*\*|The mobile phone number of the RAM user. |
|UpdateDate|String|2015-02-11T03:15:21Z|The time when the information about the RAM user was updated. |
|UserId|String|122748924538\*\*\*\*|The unique ID of the RAM user. |
|UserName|String|xiaoq\*\*\*\*|The name of the RAM user. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=UpdateUser
&UserName=zhangq****
&NewUserName=xiaoq****
&NewMobilePhone=86-1860000****
&NewEmail=xiaoq****@example.com
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
<User>
    <UserId>122748924538****</UserId>
    <UserName>xiaoq****</UserName>
    <DisplayName>xiaoq*****</DisplayName>
    <MobilePhone>86-1860000****</MobilePhone>
    <Email>xiaoq****@example.com</Email>
    <Comments>This is a cloud computing engineer.</Comments>
    <CreateDate>2015-01-23T12:33:18Z</CreateDate>
    <UpdateDate>2015-02-11T03:15:21Z</UpdateDate>
</User>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "User": {
        "UserId": "122748924538****",
        "UserName": "xiaoq****",
        "DisplayName": "xiaoq*****",
        "MobilePhone": "86-1860000****",
        "Email": "xiaoq****@example.com",
        "Comments": "Cloud computing engineer",
        "CreateDate": "2015-01-23T12:33:18Z",
        "UpdateDate": "2015-02-11T03:15:21Z"
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram).

