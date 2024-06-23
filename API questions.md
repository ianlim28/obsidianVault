**How are REST APIs Stateless?**

REST APIs are stateless, meaning that each request from a client to a server must contain all the information needed to understand and process the request. The server does not store any context or session information between requests. This statelessness simplifies server design, increases scalability, and makes it easier to distribute the system across multiple servers.

**HTTP Methods**

HTTP methods are the actions performed on resources in a RESTful API. The most commonly used HTTP methods are:  

1. **GET**: Retrieve a resource.
• **Example**: GET /users/1 retrieves the user with ID 1.

2. **POST**: Create a new resource.
• **Example**: POST /users creates a new user.

3. **PUT**: Update an existing resource completely.
• **Example**: PUT /users/1 updates the user with ID 1.

4. **PATCH**: Update a part of an existing resource.
• **Example**: PATCH /users/1 updates part of the user with ID 1.

5. **DELETE**: Delete a resource.
• **Example**: DELETE /users/1 deletes the user with ID 1.

  

**HTTP Status Codes**

HTTP status codes are issued by a server in response to a client’s request made to the server. They indicate whether the request was successfully processed or if there was an error. Common status codes include:

  

• **200 OK**: The request was successful.
• **201 Created**: The request was successful, and a resource was created.
• **204 No Content**: The request was successful, but there is no content to send in the response.
• **400 Bad Request**: The request was invalid or cannot be served.
• **401 Unauthorized**: The request requires user authentication.
• **403 Forbidden**: The server understood the request but refuses to authorize it.
• **404 Not Found**: The requested resource could not be found.
• **500 Internal Server Error**: The server encountered an unexpected condition that prevented it from fulfilling the request.

**URI (Uniform Resource Identifier)**

A **Uniform Resource Identifier (URI)** is a string of characters used to identify a resource on the internet. URIs are fundamental to the World Wide Web and can be used to locate or name a resource. There are two main types of URIs: URLs (Uniform Resource Locators) and URNs (Uniform Resource Names).

**Components of a URI**

1. **Scheme**: Indicates the protocol to be used to access the resource. Examples include http, https, ftp, mailto, etc.
2. **Authority**: Consists of three parts:
• **User Info (optional)**: Contains user credentials, usually in the format username:password.
• **Host**: The domain name or IP address of the server where the resource is located.
• **Port (optional)**: The port number on the server, separated from the host by a colon.
3. **Path**: Specifies the specific resource within the host that the URI is pointing to. The path is often hierarchical and separated by slashes.
4. **Query (optional)**: Contains data to be sent to the server, often in the form of key-value pairs separated by &, starting with a ?.
5. **Fragment (optional)**: Refers to a specific part of the resource, usually preceded by a #.

  

**Best Practices in Making the URI for RESTful Web Services**

1. **Use Nouns, Not Verbs**: URIs should represent resources, so use nouns.
• **Example**: /users instead of /getUsers.

2. **Use Plural Nouns**: For collections of resources.
• **Example**: /users for a list of users.

3. **Use HTTP Methods**: To specify actions, not in the URI.
• **Example**: GET /users to get users, POST /users to create a user.

4. **Hierarchical Structure**: Reflect resource hierarchy.
• **Example**: /users/{userId}/posts for posts of a user.

5. **Consistent Naming Conventions**: Use lower case and hyphens for readability.
• **Example**: /user-accounts instead of /userAccounts.

6. **Avoid File Extensions**: URIs should not include file extensions.
• **Example**: /users instead of /users.json.

Differences between REST and SOAP
Differences between REST and AJAX

**Tools Used to Develop and Test REST APIs**

1. **Postman**: Popular tool for testing APIs with a user-friendly interface.
2. **Swagger**: Tool for designing, building, and documenting REST APIs.
3. **Insomnia**: Another powerful REST API client for testing and debugging APIs.
4. **cURL**: Command-line tool for making HTTP requests, often used for testing APIs.
5. **JMeter**: Used for performance testing of APIs.
6. **API Gateway**: AWS API Gateway, Apigee, and others for managing and scaling APIs.
7. **Newman**: A command-line tool to run Postman collections.

**Pros and Cons of REST APIs**

**Pros**

1. **Scalability**: Statelessness makes it easy to scale.
2. **Flexibility**: Supports multiple formats like JSON, XML, HTML.
3. **Performance**: Lightweight and efficient due to minimal overhead.
4. **Interoperability**: Can be used across different platforms and languages.
5. **Easy to Use**: Simple to understand and implement.

**Cons**

1. **Statelessness**: Can lead to redundant data transfer, increasing overhead.
2. **Lack of Standardization**: No strict standards, which can lead to inconsistencies.
3. **Security**: Relies on underlying transport protocol (HTTP/HTTPS) for security.
4. **Complexity in Handling**: Some operations, like batch processing, can be more complex compared to stateful approaches.