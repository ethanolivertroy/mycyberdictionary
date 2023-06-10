# HTTP Status Codes

HTTP status codes are three-digit numbers that indicate the outcome of an HTTP request. They are grouped into classes based on the first digit.


**1xx (Informational)**: The request was received, and the server is continuing to process it.

**2xx (Successful)**: The request was successfully received, understood, and accepted.
- **200 OK**: The request has succeeded, and the server has returned the requested data.
- **201 Created**: The request has been fulfilled, and a new resource has been created as a result.
- **204 No Content**: The request has succeeded, but there's no additional information to send back. Typically used for DELETE requests.

**3xx (Redirection)**: Further action is needed to complete the request.
- **301 Moved Permanently**: The requested resource has been permanently moved to a new location. Clients should update their links and use the new URL for future requests.
- **302 Found** (Previously "Moved Temporarily"): The requested resource has been temporarily moved to a new location. Clients should use the new URL for this request but continue using the original URL for future requests.
- **307 Temporary Redirect**: Similar to 302, but requires the client to use the same HTTP method for the redirected request.

**4xx (Client Error)**: The request contains bad syntax or cannot be fulfilled by the server.
- **400 Bad Request**: The request is malformed or invalid. The server cannot process the request.
- **401 Unauthorized**: The request requires authentication, and the client has failed to provide valid credentials.
- **403 Forbidden**: The client does not have permission to access the requested resource. Unlike 401, authentication will not help.
- **404 Not Found**: The requested resource could not be found on the server.
- **405 Method Not Allowed**: The HTTP method used in the request is not supported for the requested resource.

**5xx (Server Error)**: The server failed to fulfill a valid request.
- **500 Internal Server Error**: A generic error message indicating that the server encountered an error while processing the request.
- **502 Bad Gateway**: The server, acting as a gateway or proxy, received an invalid response from an upstream server while processing the request.
- **503 Service Unavailable**: The server is temporarily unable to handle the request, usually due to maintenance or overloading.
- **504 Gateway Timeout**: The server, acting as a gateway or proxy, did not receive a timely response from an upstream server and cannot complete the request.
