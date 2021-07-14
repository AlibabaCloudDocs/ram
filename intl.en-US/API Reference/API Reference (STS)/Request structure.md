# Request structure

This topic describes the details about the request structure. The details include the endpoints of Security Token Service \(STS\), communications protocols, HTTPS request methods, and request parameters.

## Endpoints

For information about STS endpoints, see [Endpoints](/intl.en-US/API Reference/API Reference (STS)/Endpoints.md).

## Protocols

To ensure communication security, STS allows you to send requests only over HTTPS.

## Methods

STS allows you to send HTTPS GET and POST requests.

**Note:** The size of each HTTPS GET request cannot exceed 4 KB. The size of each HTTPS POST request cannot exceed 10 MB.

## Parameters

You must configure the following parameters for each API request:

-   The Action parameter. This parameter specifies the operation that you want to call.
-   The common request parameters. For more information, see [Common parameters](/intl.en-US/API Reference/API Reference (STS)/Common parameters.md).
-   The request parameters that are specific to the API operation.

## Encoding

Requests and responses are encoded in UTF-8.

