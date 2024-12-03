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

 - **Resource(s)**: Anything that can be accessed of manipulated (ex: videos, blog entries, user profiles, images, people, devices). Can be related to other resources, can have multiple, & can be grouped into collections.
  - **URI**(Uniform Resource Identifier): Used to indentify resources before interacting & using.
    - scheme:scheme-specific-part (syntax)
    - 1st "scheme": used to define semantics and interpretation of rest of URI (ex: http, ftp, mailto, etc.)
    - *HTTP ex*: [URI] http://blog.example.com/posts -> [Resource Description] Represents a collection of blog post resources.
    - Can contain path variable/template variable using {} (ex:http//blog.example.com/**{year}**/posts).
  - **Representation**: Snapshot of resources state at given time.
    - Can be text-based formats (ex: HTML, XML, JSON, etc.) or binary formats (ex: PDF, JPEG, MP4, etc.).
    - Content Negotiation: Client request for specific representation (using formats above).
   
### HTTP
  - **HTTP Methods**: Allow client & server interaction through standardized operations (verbs).
    - 2 important characteristics: Safety & Indempotency 
      - *Safety*: HTTP methods that don't cause server state changes. Mostly read-only & may return different values.
      - *Indempotency*: Operation produces same server state regardless of the # of times applied.
    - **GET, POST, PUT, DELETE,** etc. (4 of 8)
    - **GET** (safe & idempotent): Used to retrieve resource's representation. Includes metadata, which is represented by HTTP Headers (sequence of key value pairs).
    - **HEAD** (safe & idempotent): Check if resource exists w/out representation (metadata only). Uses less bandwidth than GET.
    - **DELETE** (idempotent): Requests a resource to be deleted. Use causes GET to then return 404 on resource.
    - **PUT** (idempotent): Allows client to modify resource state & update representation (replace previous state). Returns 200 upon success.
    - **POST** (n/a): Used to create resources. Does not need URI, server will assign ID.
    - **PATCH** (n/a): Used to perform partial resource updates. Can be done in different formats.
  - **CRUD** : 4 basic persistence functions for mapping data-driven apps -> **C**reate, **U**pdate, **R**ead, **D**elete.
  - **HTTP Status Codes**: Allows server to communicate results of client's request.
    - Informational Codes: Request received, but processing not complete [100]
      - 100 (Continue)
    - Success Codes: Request successfully received & processed [200]
      - 200 (OK)
      - 201 (Created)
      - 202 (Accepted)
      - 204 (No content) 
    - Redirection Codes: Request processed, but additional action required for completion [300]
      - 301 (Moved Permanently)
    - Client Error Codes: Error with client request [400]
      - 400 (Bad Request)
      - 401 (Unauthorized)
      - 403 (Forbidden)
      - 404 (Not Found)
      - 406 (Not Acceptable)
    - Server Error Codes: Server error while processing client request [500]
      - 500 (Internal Server Error)
      - 503 (Service Unavailable)
### Steps to Build RESTful API
Identify:
  1) Resources
  2) Endpoints
  3) Actions
  4) Responses

### Spring Framework
- Dependency Injection: Allows dependencies to be injected into components that need them)
- Spring Web MVC
  - MVC = Model View Controller Pattern: used for building decoupled Web applications
  - Model: Represents data/state.
  - View: Visual representation of model.
  - Controller: Responsible for handlic user actions. Interacts with services/repositories.
    

