### 1. What is a REST API?

**REST API = communication using HTTP**

- **Resource** = business entity exposed through API
- **URL** = identifies the resource
- **Methods** = GET, POST, PUT, PATCH, DELETE
- **Response** = usually JSON (data format)
- **Stateless** = each request is independent

---

### 2. What is a resource in REST?

**Resource = entity exposed through an API**

- **Example** = `/users/123`
- **User** = resource
- **123** = resource identifier

---

### 3. What are the HTTP methods in REST?

**HTTP methods = define the operation**

- **GET** = read resource
- **POST** = create resource
- **PUT** = replace resource
- **PATCH** = partially update resource
- **DELETE** = remove resource

---

### 4. What is the difference between PUT and PATCH?

**PUT = replace, PATCH = partially update**

- **PUT** = sends complete resource
- **PATCH** = sends changed fields
- **Idempotent** = same request gives same final state
- **PUT** = idempotent
- **PATCH** = generally used for partial updates

---

### 5. What is statelessness in REST?

**Stateless = server doesn't store client state**

- **State** = information about previous interactions
- **Stateless** = every request contains required information
- **Server** = doesn't depend on previous requests
- **Example** = authentication token sent with every request

---

### 6. What are HTTP status codes?

**Status code = tells the result of a request**

- **2xx** = successful request
- **4xx** = client-side error
- **5xx** = server-side error
- **200** = successful request
- **201** = resource created
- **204** = success with no body
- **400** = invalid request
- **401** = authentication required/failed
- **403** = access not allowed
- **404** = resource not found
- **409** = resource conflict
- **500** = server error

---

### 7. What is the difference between 401 and 403?

**401 = authentication problem, 403 = authorization problem**

- **Authentication** = verifying who you are
- **Authorization** = checking what you can access
- **401** = identity not established
- **403** = identity known but access denied

---

### 8. What is the difference between 200 and 201?

**200 = successful operation, 201 = resource created**

- **200** = request successfully completed
- **201** = new resource successfully created
- **Example** = `POST /users` → `201 Created`

---

### 9. What is idempotency?

**Idempotency = repeated request produces same final state**

- **Idempotent** = repeated execution doesn't change final result
- **GET** = idempotent
- **PUT** = idempotent
- **DELETE** = idempotent
- **POST** = generally not idempotent

---

### 10. What is the difference between POST and PUT?

**POST = create, PUT = replace**

- **POST** = `POST /users`
- **PUT** = `PUT /users/123`
- **POST** = server commonly generates ID
- **PUT** = client knows resource URL

---

### 11. How should REST URLs be designed?

**REST URL = represents a resource, not an action**

- **Good** = `/users/123/orders`
- **Bad** = `/getUserOrders`
- **Collection** = `/users`
- **Single resource** = `/users/123`

---

### 12. What is a path parameter?

**Path parameter = identifies a specific resource**

- **Example** = `/users/123`
- **123** = path parameter
- **Use** = identify the user

---

### 13. What is a query parameter?

**Query parameter = modifies or filters a request**

- **Filtering** = `?status=active`
- **Sorting** = `?sort=name`
- **Pagination** = `?page=2&limit=20`
- **Searching** = `?q=harshit`

---

### 14. Path parameter vs query parameter?

**Path = identify, query = filter/customize**

- **Path** = `/users/123`
- **Query** = `/users?role=admin`
- **Path** = identifies the resource
- **Query** = modifies the result

---

### 15. What is API versioning?

**API versioning = managing API changes without breaking clients**

- **Version** = identifies API contract (expected API structure)
- **Example** = `/api/v1/users`
- **Purpose** = support old and new clients
- **Common approach** = URL-based versioning

---

### 16. What is pagination?

**Pagination = returning large data in smaller chunks**

- **Page** = requested result position
- **Limit** = number of records returned
- **Example** = `?page=2&limit=20`
- **Benefit** = reduces response and database load

---

### 17. Offset vs cursor pagination?

**Offset = position-based, cursor = continuation-based**

- **Offset** = `?offset=100&limit=20`
- **Cursor** = `?cursor=abc123`
- **Offset** = simpler to implement
- **Cursor** = better for large/changing datasets
- **Cursor** = points to where the next page starts

---

### 18. What is authentication in REST?

**Authentication = verifying client identity**

- **JWT** = signed token containing claims
- **API Key** = client identification key
- **OAuth** = delegated authorization framework
- **Header** = commonly `Authorization: Bearer <token>`

---

### 19. What is authorization?

**Authorization = deciding what an authenticated client can do**

- **Authentication** = who are you?
- **Authorization** = what can you do?
- **Role** = permission category like admin/user
- **Example** = only admins can delete users

---

### 20. What are HTTP headers?

**Headers = metadata sent with HTTP requests/responses**

- **Authorization** = authentication information
- **Content-Type** = body format
- **Accept** = expected response format
- **Cache-Control** = caching instructions

---

### 21. What is Content-Type?

**Content-Type = format of the request/response body**

- **JSON** = `application/json`
- **Form data** = `multipart/form-data`
- **Purpose** = tells receiver how to interpret body

---

### 22. What is the Accept header?

**Accept = response formats the client can handle**

- **Example** = `Accept: application/json`
- **Meaning** = client expects JSON response
- **Content-Type** = format being sent
- **Accept** = format being requested

---

### 23. What is API validation?

**Validation = checking whether input is acceptable**

- **Required fields** = check presence
- **Data type** = check expected type
- **Format** = check structure
- **Business rule** = check domain requirement
- **Invalid input** = return appropriate `4xx`

---

### 24. Where should validation happen?

**Validation = primarily at the API boundary**

- **Controller** = basic input validation
- **Service** = business validation
- **Database** = data integrity constraints
- **Principle** = never trust client input

---

### 25. What is rate limiting?

**Rate limiting = restricting request frequency**

- **Limit** = maximum requests allowed
- **Example** = 100 requests/minute
- **Purpose** = prevent abuse and overload
- **Common tool** = Redis (in-memory data store)

---

### 26. What is API caching?

**Caching = temporarily storing frequently used data**

- **Cache** = fast temporary storage
- **Example** = Redis
- **Benefit** = reduces database requests
- **Trade-off** = stale data (outdated value)

---

### 27. What is the difference between REST and SOAP?

**REST = architectural style, SOAP = communication protocol**

- **REST** = commonly uses JSON
- **SOAP** = uses XML
- **REST** = simpler HTTP-based APIs
- **SOAP** = strict standards and contracts

---

### 28. What makes a REST API production-ready?

**Production-ready API = correctness + security + reliability + observability**

- **Correctness** = validation + proper status codes
- **Security** = authentication + authorization
- **Reliability** = timeouts + controlled retries
- **Performance** = pagination + caching
- **Observability** = logs + metrics + tracing (tracking request flow)

---

### 29. What is a REST API endpoint?

**Endpoint = specific URL where an API operation is available**

- **URL** = identifies API location
- **Method** = defines operation
- **Example** = `GET /users/123`
- **Endpoint** = method + URL combination

---

### 30. What is the difference between an API and an endpoint?

**API = complete interface, endpoint = specific access point**

- **API** = collection of available operations
- **Endpoint** = one specific operation
- **Example API** = User API
- **Endpoint** = `GET /users/123`

---

### 31. What is a request body?

**Request body = data sent from client to server**

- **Used with** = POST, PUT, PATCH
- **Example** = `{ "name": "Harshit" }`
- **Format** = commonly JSON
- **GET** = generally doesn't require a body

---

### 32. What is a response body?

**Response body = data returned by the server**

- **Example** = user details
- **Format** = commonly JSON
- **Success** = contains requested/created data when appropriate
- **Error** = can contain error details

---

### 33. What is API contract?

**API contract = agreed structure between client and server**

- **Defines** = URL, method, request, response
- **Defines** = status codes and errors
- **Purpose** = client and server compatibility
- **Example** = OpenAPI (standard API specification)

---

### 34. What is OpenAPI/Swagger?

**OpenAPI = standard way to describe REST APIs**

- **Defines** = endpoints and methods
- **Defines** = request/response schemas
- **Swagger UI** = interactive API documentation
- **Benefit** = easier development and testing

---

### 35. What is a good REST API response structure?

**Response structure = consistent format across APIs**

```json
{
  "data": {},
  "message": "User fetched successfully"
}
```

- **data** = actual response
- **message** = human-readable information
- **Consistency** = same structure across endpoints
- **Errors** = should have a predictable error structure

---

### 36. How do you design error responses?

**Error response = consistent and useful failure information**

```json
{
  "code": "USER_NOT_FOUND",
  "message": "User not found"
}
```

- **Code** = machine-readable identifier
- **Message** = human-readable explanation
- **Status** = HTTP status code
- **Avoid** = exposing internal implementation details

---

### 37. How do you secure a REST API?

**REST security = authenticate + authorize + validate + protect**

- **Authentication** = verify client identity
- **Authorization** = verify permissions
- **HTTPS** = encrypt network communication
- **Validation** = reject malicious/invalid input
- **Rate limiting** = control request frequency
- **Secrets** = never expose credentials in responses

---

### 38. How do you make REST APIs scalable?

**Scalable API = stateless + efficient + horizontally scalable**

- **Stateless** = requests can go to any server
- **Load balancer** = distributes requests
- **Caching** = reduces database load
- **Pagination** = controls response size
- **Database optimization** = improves query performance
- **Horizontal scaling** = add more server instances

---

### 39. What happens when a client calls a REST API?

**Request → Load Balancer → API Server → Service → Database → Response**

- **Client** = sends HTTP request
- **Load Balancer** = selects server
- **API Server** = handles request
- **Service** = executes business logic
- **Database** = reads/writes data
- **Response** = returned to client

---

### 40. What are common REST API mistakes?

**Common mistakes = inconsistent, insecure, or inefficient APIs**

- **URLs** = using actions instead of resources
- **Status codes** = returning `200` for every situation
- **Security** = trusting client input
- **Pagination** = returning thousands of records
- **Errors** = inconsistent error structures
- **Versioning** = breaking existing clients without migration strategy
