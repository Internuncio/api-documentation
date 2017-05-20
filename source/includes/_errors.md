# Errors

Hitblocks uses conventional HTTP response codes to indicate the success or
failure of an API request. Codes in 2xx range are successful, codes in the 4xx
range indicate a user based error, and codes in 5xx range indicate an error on Hitblock's
servers.

##Error codes

The Hitblocks API uses the following error codes:


Error Code | Meaning
---------- | -------
**200 - OK** | Everything worked as expected
**400 - Bad Request** | Your request sucks
**401 - Unauthorized** | Your API key is wrong
**403 - Forbidden** | The resource requested is not available for your account
**404 - Not Found** | The requested resource could not be found
**405 - Method Not Allowed** | You tried to access a resource with an invalid method
**406 - Not Acceptable** | You requested a format that isn't JSON
**410 - Gone** | The resource requested has been removed from our servers
**429 - Too Many Requests** | You're requesting too many resources at once! Slow down!
**500 - Internal Server Error** | We had a problem with our server. Try again later.
**503 - Service Unavailable** | We're temporarily offline for maintenance. Please try again later.


##Error types

There is also a body response that contains more detailed information about
specific errors that you can look up here.

###Errors

Types | Meaning
----- | -------
**api_connection_error** | Failure to connect to Hitblock's API.
**api_error** | API errors cover any other type of problem (e.g., a temporary problem with Hitblock's servers) and are extremely uncommon.
**authentication_error** | Failure to properly authenticate yourself in the request.
**invalid_request_error** | Invalid request errors arise when your request has invalid parameters.
**rate_limit_error** | Too many requests hit the API too quickly.
**validation_error** | Errors triggtered by our interfaces when failing to validate incoming properties.


##Handling errors

Our API libraries will try to raise exceptions for any of the reasons above, but
we recommend you write code that handles all possible API exceptions.
