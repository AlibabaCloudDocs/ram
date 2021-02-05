# Request signatures

You must sign all API requests to ensure security. Alibaba Cloud uses the request signature to verify the identity of the API caller. Each API request must contain the signature, regardless of whether it is sent over HTTP or HTTPS.

## Overview

For an RPC API, you must add the signature to the API request in the following format:

```
https://Endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

In the preceding format:

-   SignatureMethod: the encryption algorithm used to calculate the signature. Set the value to HMAC-SHA1.
-   SignatureVersion: the version of the signature encryption algorithm. Set the value to 1.0.
-   SignatureNonce: a unique, random number used to prevent replay attacks. You must use different random numbers for different requests. We recommend that you use universally unique identifiers \(UUIDs\).
-   Signature: the signature generated after the request has been symmetrically encrypted by using the AccessKey secret.

The signature encryption algorithm complies with RFC 2104 HMAC-SHA1 specifications. The AccessKey secret is used to calculate the hash-based message authentication code \(HMAC\) value of the encoded and sorted query string, and the HMAC value is used as the signature string. Request signatures include operation-specific parameters. Therefore, the signature of a request varies based on the request parameters. To calculate a signature, follow the steps in this topic.

```
Signature = Base64( HMAC-SHA1( AccessKey Secret, UTF-8-Encoding-Of(StringToSign)) )
```

## Step 1: Compose and encode a string-to-sign

1.  Use request parameters to construct a canonicalized query string.
    1.  by arranging the request parameters \(including all common and operation-specific parameters except Signature\) in alphabetical order.

        **Note:** If you use the GET method to submit the request, these parameters are the part located after the question mark \(?\) and connected by the ampersands \(&\) in the request uniform resource identifier \(URI\).

    2.  Encode the names and values of the arranged request parameters in the request URL by using the unicode transformation format \(UTF\)-8 character set. The following table describes the encoding rules.

        |Character|Encoding rule|
        |---------|-------------|
        |Uppercase letters, lowercase letters, digits, hyphens \(-\), underscores \(\_\), periods \(.\), and tildes \(~\)|These characters do not need to be encoded.|
        |Other characters|These characters must be percent encoded in `%XY` format. `XY` represents the ASCII code of the characters in hexadecimal notation. For example, double quotation marks \("\) are encoded as `%22`.|
        |Extended UTF-8 characters|These characters are encoded in `%XY%ZA...` format.|
        |Space characters|Spaces must be encoded as `%20`. Do not encode spaces as plus signs \(+\). This encoding method is different from the `application/x-www-form-urlencoded` MIME encoding algorithm \(such as the `java.net.URLEncoder` class provided by the Java standard library\). However, you can apply the encoding algorithm and replace the plus sign \(+\) in the encoded string with `%20`, the asterisk \(\*\) with `%2A`, and `%7E` with the tilde \(~\). To do this, you can use the following `percentEncode` method:

        ```
private static final String ENCODING = "UTF-8";
private static String percentEncode(String value) throws UnsupportedEncodingException 
{
return value ! = null ? URLEncoder.encode(value, ENCODING).replace("+", "%20").replace("*", "%2A").replace("%7E", "~") : null;
}
        ``` |

    3.  Connect the encoded parameter names and their values by using equal signs \(=\).
    4.  Sort the connected parameter name and value pairs in the order specified in step i and connect the pairs by using ampersands \(&\) to obtain the canonicalized query string.
2.  Use the canonicalized query string to construct a string-to-sign in the following way:

    ```
    StringToSign=
          HTTPMethod + "&" +
          percentEncode("/") + "&" +
           percentEncode(CanonicalizedQueryString)
    ```

    In the preceding rules:

    -   HTTPMethod: the HTTP method used to submit a request, such as GET.
    -   percentEncode\("/"\): specifies the encoded value \(%2F\) of a forward slash \(/\). The encoding follows the URL encoding rules.
    -   percentEncode\(CanonicalizedQueryString\): specifies the encoded canonicalized query string based on the URL encoding rules.

## Step 2: Calculate the signature string

1.  Calculate the HMAC value of the string-to-sign based on RFC 2104.

    **Note:** Use the SHA1 algorithm to calculate the HMAC value of the string-to-sign. The combination of your AccessKey secret and an ampersand \(&\) \(ASCII code 38\) that follows the secret is used as the key for the HMAC calculation.

2.  Encode the HMAC value in Base64 to obtain the signature string
3.  Add the signature string to the request as the Signature parameter.

    **Note:** When the obtained signature value is submitted as the final request parameter value, the value must be URL-encoded like other parameters based on rules defined in [RFC 3986](https://tools.ietf.org/html/rfc3986).


## Signature example

This section uses the CreateUser operation as an example to introduce the signature method.

Request URL before the request is signed:

```
https://ims.aliyuncs.com/?&Action=CreateUser&UserPrincipalName=test@example.onaliyun.com&DisplayName=test&SignatureVersion=1.0&Format=JSON&Timestamp=2021-01-15T06:02:28Z&AccessKeyId=testid&SignatureMethod=HMAC-SHA1&Version=2019-08-15&SignatureNonce=3f6b4e80-56f7-11eb-a256-a9f756ea7e85
```

The `StringToSign`:

```
GET&%2F&AccessKeyId%3Dtestid%26Action%3DCreateUser%26DisplayName%3Dtest%26Format%3DJSON%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3D3f6b4e80-56f7-11eb-a256-a9f756ea7e85%26SignatureVersion%3D1.0%26Timestamp%3D2021-01-15T06%253A02%253A28Z%26UserPrincipalName%3Dtest%2540example.onaliyun.com%26Version%3D2019-08-15
```

Assume that the AccessKey ID is testid and the AccessKey secret is testsecret. The key that is used to calculate the HMAC value of the string-to-sign is testsecret&.

The calculated signature string is `02heLegtw4+BFamznl1Ltj+vJ4A=`.

Request URL after the request is signed:

```
https://ims.aliyuncs.com/?Signature=02heLegtw4%2BBFamznl1Ltj%2BvJ4A%3D&AccessKeyId=testid&Action=CreateUser&DisplayName=test&Format=JSON&SignatureMethod=HMAC-SHA1&SignatureNonce=3f6b4e80-56f7-11eb-a256-a9f756ea7e85&SignatureVersion=1.0&Timestamp=2021-01-15T06%3A02%3A28Z&UserPrincipalName=test%40example.onaliyun.com&Version=2019-08-15
```

