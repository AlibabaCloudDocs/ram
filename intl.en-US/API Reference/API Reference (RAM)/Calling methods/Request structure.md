# Request structure

This topic describes the details about the request structure, including the endpoints of Resource Access Management \(RAM\), communications protocols, HTTPS request methods, and request parameters.

## Endpoints

The RAM endpoint is `https://ram.aliyuncs.com`.

## Protocols

To ensure communication security, RAM allows you to send requests only over HTTPS.

## Methods

RAM allows you to send HTTPS GET and POST requests.

**Note:** The size of each HTTPS GET request cannot exceed 4 KB. The size of each HTTPS POST request cannot exceed 10 MB.

## Parameters

You must configure the following parameters for each API request:

-   The Action parameter. This parameter specifies the operation that you want to call.
-   The common request parameters. For more information, see [Common parameters](/intl.en-US/API Reference/API Reference (RAM)/Calling methods/Common parameters.md).
-   The request parameters that are specific to the API operation.

## Encoding

Requests and responses are encoded in UTF-8.

