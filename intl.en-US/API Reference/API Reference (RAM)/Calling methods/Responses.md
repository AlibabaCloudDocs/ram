# Responses

After RAM API operations are called, data is returned in a unified format. The returned data is in either the XML or JSON format, and the XML format is the default option. Sample responses in API documents are formatted in a way that is easier for you to read. The actual responses are not formatted with line breaks or indentation.

## Sample success responses

An HTTP status code `2xx` indicates that the API operation is successful.

-   XML format

    ```
    <?xml version="1.0" encoding="utf-8"? >
    <!-Result root node-->
    <API operation name+Response>
        <!-Request ID-->
        <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
        <!-Returned data-->
    </Operation name+Response>
    ```

-   JSON format

    ```
    {
        "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
        /* Returned data */
    }
    ```


## Sample error responses

An HTTP status code `4xx` or `5xx` indicates that the API operation fails and no result data is returned. The returned message body contains the specific error code, error message, the `RequestId` parameter, and the `HostId` parameter. The `RequestId` parameter indicates the globally unique ID of the API request. The `HostId` parameter indicates the ID of the host to which your API request is sent. You can locate the errors by using the error code. For more information, see [Error codes](https://error-center.aliyun.com/status/product/Ram).

-   XML format

    ```
    <?xml version="1.0" encoding="UTF-8"? >
    <Error>
       <RequestId>8906582E-6722-409A-A6C4-0E7863B733A5</RequestId>
       <HostId>ram.aliyuncs.com</HostId>
       <Code>InvalidParameter</Code>
       <Message>The specified parameter "Action or Version" is not valid. </Message>
    </Error>
    ```

-   JSON format

    ```
    {
        "RequestId": "7463B73D-35CC-4D19-A010-6B8D65D242EF",
        "HostId": "ram.aliyuncs.com",
        "Code": "InvalidParameter",
        "Message": "The specified parameter \"Action or Version\" is not valid."
    }
    ```


