# API Design Patterns

Let's define REST API. The definition of a RESTful API means you don’t need to use the HTTP protocol. However, the two developed alongside each other, and almost every RESTful API code relies upon HTTP. For that reason, it makes sense to structure your API around the built-in methods and status codes that are already well-defined in HTTP. Here's how you can design, develop, and create an HTTP REST API.

## Status Codes

Status codes, also known as HTTP response codes, are three-digit numbers that a web server sends in response to a request made by a client.

These codes provide information about the outcome of the request and help understand how the server handled it.

HTTP status codes are grouped into five main classes, each representing a general type of server response:

- 1xx - Informational Responses:
Indicate that the request has been received by the server and it is still processing the request.

- 2xx - Success Responses:
Indicate that the client's request was received, understood, and accepted by the server.

- 3xx - Redirections:
Indicate that the client needs to take additional action to complete the request. This often involves redirecting the client to another URL.

- 4xx - Client Errors:
Indicate that an error occurred in the client's request, either due to formatting issues, lack of authorization, or other client-related problems.

- 5xx - Server Errors:
Indicate that an error occurred on the server while attempting to process the client's request. This can happen for various reasons, such as server failure or application issues.

Some common HTTP status codes include:

- 100 Continue: The server has received the initial request, and the client can proceed to send the remaining data.
- 101 Switching Protocols: The server is requesting the client to switch to another protocol.
- 200 OK: The request was successful, and the response includes the requested representation, if applicable.
- 201 Created: The request was successful and resulted in the creation of a new resource.
- 204 No Content: The request was successful, but there is no content to return (commonly used in delete or update operations).
- 301 Moved Permanently: The requested resource has been permanently moved to a new location.
- 302 Found: The requested resource has been temporarily moved to a new location.
- 304 Not Modified: The client can use its cached version as the resource has not been modified since the last request.
- 400 Bad Request: The client's request is invalid or malformed.
- 401 Unauthorized: The client is not authorized to access the resource.
- 403 Forbidden: Credentials accepted but don’t have permission
- 404 Not Found: The requested resource was not found on the server.
- 410 Gone: The resource previously existed but does not now
- 429 Too many requests: Used for rate limiting and should include retry headers
- 500 Internal Server Error: An internal error occurred on the server that prevented the processing of the request.
- 502 Bad Gateway: The server, while acting as a gateway or proxy, received an invalid response from the upstream server."
- 503 Service unavailable: Another where retry headers are useful


## HTTP Methods

For designing REST APIs, Each HTTP request includes a method, sometimes called “HTTP verbs,” that provides a lot of context for each call. Here’s a look at the most common HTTP methods:

- GET: read data from your API
- POST: add new data to your API
- PUT: update existing data with your API
- PATCH: updates a subset of existing data with your API
- DELETE: remove data (usually a single resource) from your API

## Common use of HTTP Methods & Status Codes

GET /users/{id}

- 200 OK: Returns the details of the specified user.
- 404 Not Found: If the user with the specified ID is not found.

POST /users

- 201 Created: The user was successfully created.
- 400 Bad Request: The user creation request is invalid.

PUT /users/{id}

- 200 OK: The user was successfully updated.
- 201 Created: If the user does not exist and a new one is created with the specified ID.
- 404 Not Found: If the user with the specified ID is not found.
- 400 Bad Request: If the user update request is invalid.

DELETE /users/{id}

- 204 No Content: The user was successfully deleted.
- 404 Not Found: If the user with the specified ID is not found.