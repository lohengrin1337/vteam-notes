# REST API

## Part 1

[How to design a RESTful API architecture from a human-language spec](https://www.oreilly.com/content/how-to-design-a-restful-api-architecture-from-a-human-language-spec/)

* Simplicity
* Extensibillity
* Reliability
* Performance

1. Indetify nouns and verbs from the system spec
2. Extract URLs and the methods they respond to from those nouns and verbs

* Resources - nouns
* Representations - mirror the actual resource with json
* Actions - verbs

* URLs
* Media Types - json
* Methods - get, post, put, delete

* Convert verbs to nouns (eg. POST a rent)

* GET – Should be used to retrieve data from the server. Means “give me a representation of this resource identified by this URL”. It’s worth noting that we must never use GET to change resources. For this, we have the following other methods.
* POST – Should be used to provide data to the server. Means “process the resource representation as a new subordinate of this URL”. In practice, POST is mostly used for creating resources. The client specifies the resource representation in the request body and makes a POST to the URL that holds the collection of resources. 3
* PUT – Should be used to update existing server resources by replacing their old state with a new one. Means “use this representation to replace the resource identified by this URL”. 4
* DELETE – Should be used to remove server resources. Means “delete the resource identified by this URL”.

* Which HTTP methods map to our verbs?
* Which resources and corresponding URLs should we create for our nouns and noun-fied verbs?
* For each URL + method, which resource data should be included in the request body?
* For each URL + method, which resource data should be included in the response body?


## Part 2

[How a RESTful API server reacts to requests](https://www.oreilly.com/content/how-a-restful-api-server-reacts-to-requests/)


### Status codes

* 1xx – Informational responses
* 2xx – Success
    * 200 OK
        * Regular success
    * 201 Created
        * Created some resource
    * 204 No Content
        * Without a response body
* 3xx – Redirection
    * 301 Moved Permanently
        * Moved to another URL
    * 304 Not Modified
        * Caching
* 4xx – Client errors
    * 400 Bad Request
        * Invalid or malformed data
    * 401 Unauthorized
        * Wrong authentication credentials
    * 403 Forbidden
        * Insufficient permissions 
    * 404 Not Found
        * Unavailable or hidden resources
* 5xx – Server errors
    * When something wrong happens on the server, not because of client request data, but because of server state itself


### Success responses

* GET
    * 200 OK + body with resources
* POST
    * 201 Created + Location header with URL to the created resource
* PUT
    * 200 OK + body with updated resource || 204 No Content
* DELETE
    * 204 No Content


### Errors responses

* Invalid authentication
    * 401 Unauthorized + body.errors
* Wrong user input (non sensitive)
    * 400 Bad Request + body.errors
* Wrong user input (missing resource / sensitive info)
    * 404 Not Found + body.errors


### Example response

[RFC](https://www.rfc-editor.org/rfc/rfc9457.html)

{
    errors: [
        status: 400,
        title: "Invalid bike number",
        detail: "Bike with id 'xxx' is not available",
    ]
}

* Safety - a GET request should never alter server state, and thus is safe
* Idempotency - subsequent identical requests does not change resources
    * eg. after deleting a resource, a subsequent request does nothing
    * when doing subsequent POST requests, state might continue to change...


### Authentication

* Stateless auth with REST (eg. JWT rather than cookies)
* Basic
    * Authorization header with credentials (base64 encoding  of username:password)
    * Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
* Token
    * Encrypted mapping to a user
    * Authorization: Token t$IKL&qNhTfx0pr$
    * Safer than basic
* JSON Web Token
    * Authorization: Bearer xxx.xxx.xxx
* OAuth
    * Login in via social network or similar
    * Redirect to social network
    * Log in
    * Get authorization code
    * Exchange code for token
    * Access userdata through api
