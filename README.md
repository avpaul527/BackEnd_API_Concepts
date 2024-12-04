# BackEnd API Concepts
------------------------
## Spring REST (Textbook: Ch. 1 - 3)
### REST Fundamentals
- **RE***presentational* **S***tate* **T***ransfer*
- Architectual style for designing distrubuted network applications.
- **6 Constraints/Principles** (what makes an app **REST**ful)
  - **Client-Server**: *Client & Server concerns seperate, enabling client & server components to evolve independently (system = scale)*
  - **Stateless**: *Communication should allow for server to not **need** memory of client state. Client must include necessary info in request, allowing server to understand & process it.*
  - **Layered System**: *Multiple layers(ex: gateways, firewalls, proxies, etc.) can exist between client & server. To improve scalability, layers can be added, modified, reordered or removed.*
  - **Cache**: *Responses from server = cacheable || non-cacheable.  Allows client (+ components) to cache responses & reuse for later requests. Benefits = reduces load on server + improves performance.*
  - **Uniform Interface**: *Interactions between client, server, components based on interface uniformity.  Components that can evolve independently + implement agreed-on contract = Simplified architecture.
    Resource identification + resource representation + self-descriptive messages + hypermedia = 4 constraints of Uniform Interface (engine of app state [HATEOS]).*
  - **Code on Demand**(optional): *Extended functionality for clients by downloading and executing **CoD** (ex: JavaScript scripts, Java applets, Silverlight, etc.)*

 - **Resource(s)**: Anything that can be accessed of manipulated (ex: videos, blog entries, user profiles, images, people, devices, etc.). Can be related to other resources, can have multiple, & can be grouped into collections.
  - **URI**(Uniform Resource Identifier): Used to indentify resources before interacting & using.
    - scheme:scheme-specific-part (syntax)
    - 1st "scheme": used to define semantics and interpretation of rest of URI (ex: http, ftp, mailto, etc.)
    - *HTTP ex*: [**URI**] http://blog.example.com/posts -> [**Resource Description**] Represents a collection of blog post resources.
    - Can contain path variable/template variable using **{}** (ex:http//blog.example.com/**{year}**/posts).
  - **Representation**: Snapshot of resources state at given time.
    - Can be text-based formats (ex: HTML, XML, JSON, etc.) or binary formats (ex: PDF, JPEG, MP4, etc.).
    - **Content Negotiation**: Client request for specific representation (using formats above).   
### HTTP
  - **HTTP Methods**: Allow client & server interaction through standardized operations (verbs).
    - 2 important characteristics: *Safety & Indempotency*
      - *Safety*: HTTP methods that don't cause server state changes. Mostly read-only & may return different values.
      - *Indempotency*: Operation produces same server state regardless of the # of times applied.
    - **GET, POST, PUT, DELETE,** etc. (*4 of 8*)
    - **GET** (*safe & idempotent*): Used to retrieve resource's representation. Includes metadata, which is represented by HTTP Headers (sequence of key value pairs).
    - **HEAD** (*safe & idempotent*): Check if resource exists w/out representation (metadata only). Uses less bandwidth than GET.
    - **DELETE** (*idempotent*): Requests a resource to be deleted. Use causes GET to then return 404 on resource.
    - **PUT** (*idempotent*): Allows client to modify resource state & update representation (replace previous state). Returns 200 upon success.
    - **POST** (*n/a*): Used to create resources. Does not need URI, server will assign ID.
    - **PATCH** (*n/a*): Used to perform partial resource updates. Can be done in different formats.
  - **CRUD** : 4 basic persistence functions for mapping data-driven apps -> **C**reate, **U**pdate, **R**ead, **D**elete.
>  - **HTTP Status Codes**: Allows server to communicate results of client's request.
>    - Informational Codes: Request received, but processing not complete [100]
>      - 100 (*Continue*)
>    - Success Codes: Request successfully received & processed [200]
>      - 200 (*OK*)
>      - 201 (*Created*)
>      - 202 (*Accepted*)
>      - 204 (*No content*) 
>    - Redirection Codes: Request processed, but additional action required for completion [300]
>      - 301 (*Moved Permanently*)
>    - Client Error Codes: Error with client request [400]
>      - 400 (*Bad Request*)
>      - 401 (*Unauthorized*)
>      - 403 (*Forbidden*)
>      - 404 (*Not Found*)
>      - 406 (*Not Acceptable*)
>    - Server Error Codes: Server error while processing client request [500]
>      - 500 (*Internal Server Error*)
>      - 503 (*Service Unavailable*)
### Steps to Build RESTful API
*Identify*:
  1) Resources
  2) Endpoints
  3) Actions
  4) Responses
### Spring Framework
- **Dependency Injection**: Allows dependencies to be injected into components that need them.
- **Spring Web MVC**
  - **MVC** = *Model View Controller* Pattern: used for building decoupled Web applications
  - *Model*: Represents data/state, using interface.
  - *View*: Visual representation of model, using interface.
  - *Controller*: Responsible for handlic user actions. Interacts with services/repositories.
### RESTful Spring
- **Spring Boot**: Spring portfolio project that uses templates to simplify Spring application bootstrapping (includes dependencies).
> - Ways to Generate a Spring Boot Project
>  - From scratch
>  - Spring Boot starter website (http://start.spring.io)
>  - Spring Tool Suite (STS) IDE
>  - Boot CLI
- *To access & experiment REST API/apps, there are tools* (ex: Postman, RESTClient, etc.) *that allow you to test a request & inspect the response.*
-----------------------------------------------------------------------------------------------
## Rapid API (https://rapidapi.com/learn/rest)
# What is an API?
(*Application Programming Interfaces*) Specifies set of rules & protocols, and defines data format, authentication mechanisms, & other technical details for interaction between client and server.
# What is HTTP?
(*HyperText Transfer Protocol*) Application layer protocol. Provides a standardized way for applications to communicate with each other on the internet. Defines **request methods, response codes, headers,** and **message formats** used to exchange data between clients & servers.
- HTTP defines several **request methods** (*verbs*) that can be used to perform different types of actions on a resource. (*GET, POST, PUT, DELETE, PATCH, etc.*)
- HTTP defines a set of **response codes** that indicate the status of a request. These codes are three-digit numbers that are sent by the server in response to a client's request. (*200, 401, 404, etc.*)
- HTTP defines a set of **headers** that can be used to provide additional information about a request or response. Headers are key-value pairs included in the HTTP message. (*Authorization, Cache-Control, Content-Type, Accept, etc.*)
- HTTP **messages** are the way that clients and servers communicate with each other. (*Requests & Responses*). 3 parts of request are: *request line, headers, & body*. 3 parts of response are: *status line, headers, & body*.
# Different type of HTTP headers
- Request headers: *sent by the client to the server and provide additional information about the request.*
- Response headers: *sent by the server to the client and provide additional information about the response.*
- Entity headers: *sent with the entity body of a request or response and provide additional information about the content.*
# Different type of HTTP methods
1) **GET**: *used to retrieve a resource from the server. When client sends a GET request, the server responds with the requested resource.*
2) **POST**: *used to submit data to the server for processing. When client sends a POST request, the server processes the data and sends back a response.*
3) **PUT**: *used to update an existing resource on the server. When client sends a PUT request, the server replaces the existing resource with the new data provided by the client.*
4) **DELETE**: *used to delete a resource from the server. When client sends a DELETE request, the server removes the specified resource from its storage.*
5) **OPTIONS**: *used to retrieve information about the communication options available for a resource. When client sends an OPTIONS request, the server responds with a list of the available methods, headers, and other communication options for the specified resource.*
6) **HEAD**: *similar to the GET method, but only retrieves the headers for a resource and not the body. When client sends a HEAD request, the server responds with the headers for the specified resource but does not send the actual content.*
7) **CONNECT**: *used to establish a network connection to a resource. When client sends a CONNECT request, the server responds with a tunnel that can be used to establish a secure connection to the specified resource.*
8) **TRACE**: *used to retrieve a diagnostic trace of the communication between a client and a server. When a client sends TRACE request, the server responds with a message that contains a copy of the request and response headers.*
# What is a REST API?
**REST** (**RE**presentational **S**tate **T**ransfer) APIs allow computers to talk to each other over the internet in a way that is standardized and easy to understand.
- Software architectural style for building web services that allow communication between applications over the internet.
-  Emphasizes simplicity, scalability, and flexibility.
# Key feature of REST APIs
Allow applications to interact with each other over the internet by sending and receiving data in a standardized way. Allow applications to communicate without being tightly coupled (changes to one application won't necessarily impact the other application).
Key features:
- Client-server architecture




