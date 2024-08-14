
#### <span style="color:green">What is an API Call?</span>
An **API call** is a request made to an API to access data or functionality. A client makes an API call and sends a request to the API server, and the server sends back a response. The request and response use a specific format and structure and are transmitted using a specific protocol (such as HTTP).

#### <span style="color:green">What is an API Endpoint?</span>
An **API endpoint** is a specific location on a server that can receive and respond to API requests. An API endpoint is identified by a URI (Uniform Resource Identifier) and is typically associated with a particular API or service.


#### <span style="color:green">Differences Between APIs and Webhooks</span>
**APIs**
• **Definition**: APIs are a set of rules and protocols that define how different software components can interact with each other. They provide a way for systems and applications to communicate, share data, and functionality.

• **Functionality**: A client sends a request to the API server using a specific protocol (like HTTP) and gets a response. The client and server communicate through a series of requests and responses, with the API defining the specific format and structure of these messages.

**Webhooks**

• **Definition**: Webhooks are a way for a server to send data to a client in real-time without the client needing to make a request.

• **Functionality**: When a specified event occurs on the server, the server sends a message to a specified URL, usually in the form of an HTTP POST request. The client processes the message and acts based on the data received. Webhooks enable real-time communication and event-driven architectures, building more efficient and responsive systems.

#### <span style="color:green">Representational State Transfer (REST) APIs</span>
**REST APIs** are a type of web API that uses HTTP requests to manipulate data. They are designed to be lightweight and flexible, ideal for building scalable and easy-to-maintain web services. REST APIs use a fixed set of HTTP verbs to perform operations on resources identified using a URI (Uniform Resource Identifier). Examples of these verbs are GET, POST, PUT, and DELETE. REST APIs are also useful for creating CRUD (Create, Read, Update, Delete) applications.

##### <span style="color:orange">Web API vs. REST API</span>
##### <span style="color:orange">Web API</span>
A Web API (Web Application Programming Interface) allows interaction between different software applications over the web.

**Protocols**:
• Can use various protocols such as HTTP, HTTPS, SOAP, and more.

**Formats**:
• Data exchanged can be in various formats, including JSON, XML, HTML, or plain text.

**Examples**:
• SOAP APIs (Simple Object Access Protocol)
• XML-RPC (XML Remote Procedure Call)
• REST APIs (Representational State Transfer)

##### <span style="color:orange">Rest API</span>
A REST API adheres to the principles of Representational State Transfer (REST), an architectural style for networked applications.

**Principles of REST**:
- **Stateless**: Each request from client to server must contain all information needed to understand and process the request. No client context is stored on the server between requests.

- **Client-Server Architecture**: The client and server are separate and communicate over a network, typically using HTTP.

- **Cacheable**: Responses from the server can be cached to improve performance.

- **Layered System**: A client cannot ordinarily tell whether it is connected directly to the end server or an intermediary along the way.

- **Uniform Interface**: REST APIs use standard HTTP methods (GET, POST, PUT, DELETE) and resource URIs to perform operations.

**Formats**:
- Typically use JSON (JavaScript Object Notation) for data exchange, but can also use XML, HTML, or plain text.

**Examples**:
- Most modern web services, such as those provided by Google, Facebook, Twitter, and GitHub, use REST APIs.

##### <span style="color:orange">Key Differences Btw Web and REST API</span>
 **Scope**:
- **Web API**: General term encompassing any API operating over the web, using various protocols and formats.

- **REST API**: A subset of Web APIs that strictly follows REST principles and usually operates over HTTP/HTTPS.

**Protocols**:
- **Web API**: Can use multiple protocols, including HTTP, HTTPS, SOAP, XML-RPC, etc.
- **REST API**: Primarily uses HTTP/HTTPS protocols.

 **Architectural Style**:
- **Web API**: Not confined to a specific architectural style.
- **REST API**: Follows the REST architectural style, which includes principles like statelessness, client-server separation, and a uniform interface.

**Usage**:
- **Web API**: Can be used for a variety of purposes, including RPC (Remote Procedure Call) style interactions (like SOAP).

- **REST API**: Typically used for resource-based interactions where resources are identified by URIs and operations are performed using standard HTTP methods.

#### <span style="color:green">URI (Uniform Resource Identifier)</span>
A **Uniform Resource Identifier (URI)** is a string of characters used to identify a resource on the internet. URIs are fundamental to the World Wide Web and can be used to locate or name a resource. There are two main types of URIs: URLs (Uniform Resource Locators) and URNs (Uniform Resource Names).

##### <span style="color:orange">Components of a URI</span>
A URI typically consists of several components, which can vary depending on the type of URI. Here’s a breakdown of the common components:

- **Scheme**: Indicates the protocol to be used to access the resource. Examples include http, https, ftp, mailto, etc.
- **Authority**: Consists of three parts:
	- **User Info (optional)**: Contains user credentials, usually in the format username:password.
	- **Host**: The domain name or IP address of the server where the resource is located.
	- **Port (optional)**: The port number on the server, separated from the host by a colon.

- **Path**: Specifies the specific resource within the host that the URI is pointing to. The path is often hierarchical and separated by slashes.
- **Query (optional)**: Contains data to be sent to the server, often in the form of key-value pairs separated by &, starting with a ?.
- **Fragment (optional)**: Refers to a specific part of the resource, usually preceded by a #.

##### <span style="color:orange">Example of a URI</span>
Here’s an example URI with its components labeled:
```
https://username:password@www.example.com:8080/path/to/resource?key1=value1&key2=value2#section1
```

• **Scheme**: https
• **User Info**: username:password
• **Host**: www.example.com
• **Port**: 8080
• **Path**: /path/to/resource
• **Query**: key1=value1&key2=value2
• **Fragment**: section1

**Types of URIs**
- **URL (Uniform Resource Locator)**: Specifies the location of a resource along with the protocol needed to retrieve it. For example:
	- http://www.example.com
	- ftp://ftp.example.com/file.txt

- **URN (Uniform Resource Name)**: Identifies a resource by name in a given namespace but doesn’t specify how to locate it. For example:
	- urn:isbn:0451450523


**URI Syntax and Standards**
URIs are governed by various standards to ensure they are interpreted correctly across different systems. The most common standards are defined by the IETF (Internet Engineering Task Force) in RFC 3986.

**Importance of URIs**
• **Web Browsing**: URIs allow browsers to locate and access web pages and resources.
• **API Endpoints**: URIs are used in APIs to specify endpoints for accessing services and data.
• **Resource Identification**: URIs provide a standard way to identify resources across different systems, enabling interoperability and integration.

**Summary**
• **URI**: A string identifying a resource.
• **URL**: A type of URI that specifies the location of a resource.
• **URN**: A type of URI that names a resource without specifying its location.


Understanding URIs is crucial for working with the web, as they are the standard way to access and identify resources across the internet.


