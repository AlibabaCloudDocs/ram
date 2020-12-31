# CreateUser

Creates a RAM user.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer automatically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ram&api=CreateUser&type=RPC&version=2015-05-01)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateUser|The operation that you want to perform. Set the value to CreateUser. |
|UserName|String|Yes|zhangq\*\*\*\*|The name of the RAM user.

 The name must be 1 to 64 characters in length, and can contain letters, digits, periods \(.\), hyphens \(-\), and underscores \(\_\). |
|DisplayName|String|No|zhangq\*\*\*\*|The display name of the RAM user.

 The name must be 1 to 128 characters in length, and can contain letters, digits, periods \(.\), at signs \(@\), hyphens \(-\), and spaces. |
|MobilePhone|String|No|86-1868888\*\*\*\*|The mobile phone number of the RAM user.

 Format: <International area code\>-<Mobile phone number\> |
|Email|String|No|zhangq\*\*\*\*@example.com|The email address of the RAM user. |
|Comments|String|No|This is a cloud computing engineer.|The description of the RAM user.

 The description must be 1 to 128 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|The ID of the request. |
|User|Struct| |The information about the RAM user. |
|Comments|String|This is a cloud computing engineer.|The description of the RAM user. |
|CreateDate|String|2015-01-23T12:33:18Z|The time when the RAM user was created. |
|DisplayName|String|zhangq\*\*\*\*|The display name of the RAM user. |
|Email|String|zhangq\*\*\*\*@example.com|The email address of the RAM user. |
|MobilePhone|String|86-1868888\*\*\*\*|The mobile phone number of the RAM user. |
|UserId|String|122748924538\*\*\*\*|The unique ID of the RAM user. |
|UserName|String|zhangq\*\*\*\*|The name of the RAM user. |

## Examples

Sample requests

```
https://ram.aliyuncs.com/?Action=CreateUser
&UserName=zhangq****
&DisplayName=zhangq****
&MobilePhone=86-1868888****
&Email=zhangq****@example.com
&Comments=This is a cloud computing engineer.
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateUserResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <User>
            <UserId>122748924538****</UserId>
            <UserName>zhangq****</UserName>
            <DisplayName>zhangq****</DisplayName>
            <MobilePhone>86-1868888****</MobilePhone>
            <Email>zhangq****@example.com</Email>
            <Comments>This is a cloud computing engineer. </Comments>
            <CreateDate>2015-01-23T12:33:18Z</CreateDate>
      </User>
</CreateUserResponse>
```

`JSON` format

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "User": {
        "UserId": "122748924538****",
        "UserName": "zhangq****",
        "DisplayName": "zhangq****",
        "MobilePhone": "86-1868888****",
        "Email": "zhangq****@example.com",
        "Comments": "This is a cloud computing engineer.",
        "CreateDate": "2015-01-23T12:33:18Z"
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Ram).

After a RAM user is created, you can perform the following operations:

-   You can call the CreateLoginProfile operation to allow the RAM user to log on to the Alibaba Cloud Management Console. Then, you can configure settings for the RAM user such as logon passwords. For more information, see [CreateLoginProfile](~~28685~~).
-   You can call the CreateAccessKey operation to create an AccessKey pair for the RAM user. For more information, see [CreateAccessKey](~~28689~~).

