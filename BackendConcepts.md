# Backend Concepts — Interview Preparation

## REST APIs

### 1. What is a REST API?

**REST API = communication using HTTP**

* **Resource** = business entity exposed through API
* **URL** = identifies the resource
* **Methods** = GET, POST, PUT, PATCH, DELETE
* **Response** = usually JSON
* **Stateless** = each request is independent

---

### 2. What is GET?

**GET = retrieve data from server**

* **Purpose** = read resource
* **Body** = generally not used
* **Idempotent** = repeated request has same effect
* **Example** = `GET /users/123`

---

### 3. What is POST?

**POST = create or submit data to server**

* **Purpose** = create resource
* **Body** = commonly contains new data
* **Idempotent** = generally not idempotent
* **Example** = `POST /users`

---

### 4. What is PUT?

**PUT = replace an existing resource**

* **Purpose** = complete replacement
* **Body** = usually contains complete resource
* **Idempotent** = same request gives same final state
* **Example** = `PUT /users/123`

---

### 5. What is DELETE?

**DELETE = remove a resource**

* **Purpose** = delete resource
* **Idempotent** = generally idempotent
* **Example** = `DELETE /users/123`
* **Response** = commonly `204 No Content`

---

### 6. PUT vs PATCH?

**PUT = replace, PATCH = partially update**

* **PUT** = sends complete resource
* **PATCH** = sends changed fields
* **PUT** = idempotent
* **PATCH** = generally used for partial updates

---

# Middleware

### 7. What is middleware?

**Middleware = code that runs between request and response**

```text
Request
   ↓
Middleware
   ↓
Controller
   ↓
Response
```

* **Request** = incoming HTTP request
* **Middleware** = intercepts request/response
* **Controller** = handles endpoint logic
* **Use** = logging, authentication, CORS, rate limiting

---

### 8. Why do we need middleware?

**Middleware = centralize common request processing**

* **Logging** = record requests
* **Authentication** = verify identity
* **CORS** = control browser origins
* **Rate limiting** = restrict request frequency
* **Benefit** = avoid repeating logic in every endpoint

---

### 9. What is middleware chaining?

**Middleware chaining = execute multiple middleware sequentially**

```text
Request
  ↓
Auth
  ↓
Logger
  ↓
Rate Limiter
  ↓
Controller
```

* **Chain** = ordered middleware sequence
* **Next** = passes control forward
* **Short-circuit** = stops request early
* **Example** = unauthorized request never reaches controller

---

### 10. Middleware vs controller?

**Middleware = common request processing, controller = endpoint-specific logic**

* **Middleware** = reusable across routes
* **Controller** = handles specific endpoint
* **Middleware** = authentication/logging
* **Controller** = create user/order/etc.

---

# Authentication & Authorization

### 11. What is authentication?

**Authentication = verifying who the user is**

* **Identity** = user/client being verified
* **Credentials** = password, token, etc.
* **Example** = login with email/password
* **Result** = authenticated user

---

### 12. What is authorization?

**Authorization = checking what an authenticated user can do**

* **Authentication** = Who are you?
* **Authorization** = What can you access?
* **Role** = permission category
* **Example** = only admins can delete users

---

### 13. Authentication vs authorization?

**Authentication = identity, authorization = permissions**

* **Authentication** = happens first
* **Authorization** = happens after identity verification
* **Example** = login → authenticate → check admin permission

---

# JWT

### 14. What is JWT?

**JWT = token used to represent authenticated identity**

* **Token** = signed piece of data
* **Claims** = information stored inside token
* **Signature** = verifies token integrity
* **Server** = validates token on requests

---

### 15. What are the parts of a JWT?

**JWT = Header + Payload + Signature**

```text
xxxxx.yyyyy.zzzzz
 Header  Payload  Signature
```

* **Header** = token metadata
* **Payload** = claims/data
* **Signature** = verifies integrity
* **Important** = payload is encoded, not encrypted

---

### 16. How does JWT authentication work?

**JWT flow = login → issue token → send token → validate token**

```text
Login
  ↓
Server verifies credentials
  ↓
JWT issued
  ↓
Client sends JWT
  ↓
Server validates JWT
  ↓
Request allowed
```

* **Credentials** = login information
* **JWT** = authentication token
* **Validation** = signature/expiry checks

---

### 17. Where is JWT usually sent?

**JWT = commonly sent in Authorization header**

```http
Authorization: Bearer <token>
```

* **Authorization** = HTTP header
* **Bearer** = token authentication scheme
* **Token** = JWT value
* **Server** = extracts and validates token

---

### 18. What is JWT expiration?

**Expiration = time after which JWT should no longer be accepted**

* **`exp`** = expiration claim
* **Expired token** = authentication fails
* **Short expiry** = limits token exposure
* **Refresh token** = can obtain a new access token

---

### 19. Access token vs refresh token?

**Access token = short-lived API access, refresh token = obtain new access token**

* **Access token** = sent to APIs
* **Short-lived** = reduces exposure window
* **Refresh token** = used to renew access
* **Refresh endpoint** = issues new access token

---

### 20. JWT vs session authentication?

**JWT = client carries token, session = server stores session state**

* **JWT** = usually stateless authentication
* **Session** = server maintains session
* **JWT** = convenient for distributed services
* **Session** = easier server-side revocation
* **Choice** = depends on security and architecture

---

# Routing

### 21. What is routing?

**Routing = mapping HTTP requests to application handlers**

```text
GET /users       → getUsers()
GET /users/:id   → getUser()
POST /users      → createUser()
```

* **Route** = HTTP method + path
* **Handler** = function processing request
* **Router** = manages route mappings

---

### 22. What is route parameter?

**Route parameter = dynamic value inside URL path**

```text
/users/123
```

* **Route** = `/users/:id`
* **Parameter** = `123`
* **Purpose** = identify specific resource

---

### 23. What is route grouping?

**Route grouping = organize related endpoints under common path/middleware**

```text
/api/v1/users
/api/v1/users/:id
/api/v1/users/:id/orders
```

* **Group** = related routes
* **Prefix** = common URL portion
* **Middleware** = can apply to entire group

---

### 24. What is API versioning?

**API versioning = supporting API contract changes safely**

* **Version** = identifies API contract
* **Example** = `/api/v1/users`
* **Purpose** = avoid breaking existing clients
* **New version** = can introduce breaking changes

---

# SQL vs NoSQL

### 25. SQL vs NoSQL?

**SQL = relational data, NoSQL = non-relational data**

* **SQL** = tables + rows + relationships
* **NoSQL** = documents, key-value, graph, etc.
* **SQL** = structured schema
* **NoSQL** = often flexible schema
* **Choice** = depends on access patterns and consistency needs

---

### 26. When would you choose SQL?

**SQL = good for structured data and strong relationships**

* **Transactions** = strong ACID support
* **Relationships** = joins and foreign keys
* **Schema** = structured
* **Example** = payments, banking, order systems

---

### 27. When would you choose NoSQL?

**NoSQL = useful for flexible schemas and specific high-scale access patterns**

* **Schema** = flexible
* **Scaling** = commonly designed for horizontal scaling
* **Access pattern** = optimized around application queries
* **Example** = catalogs, event data, high-volume key-value workloads

---

### 28. What is normalization?

**Normalization = organizing relational data to reduce duplication**

* **Duplication** = repeated data
* **Normalization** = split data into related tables
* **Benefit** = consistency
* **Trade-off** = more joins

---

### 29. What is denormalization?

**Denormalization = intentionally duplicating data for faster reads**

* **Duplication** = repeated data
* **Benefit** = fewer joins
* **Read-heavy** = useful in some systems
* **Trade-off** = consistency becomes harder

---

### 30. SQL vs NoSQL: how do you decide?

**Database choice = based on data model + access patterns + consistency + scale**

* **Relationships** = favor relational model
* **Flexible data** = may favor NoSQL
* **Transactions** = often favor SQL
* **Scale** = evaluate actual workload, not database popularity

---

# ORM & ODM

### 31. What is an ORM?

**ORM = Object-Relational Mapper**

* **Object** = application object
* **Relational** = SQL database tables
* **Mapper** = connects objects to rows
* **Example** = Hibernate, SQLAlchemy, Prisma

---

### 32. Why use an ORM?

**ORM = interact with database using application objects**

* **CRUD** = simpler database operations
* **Mapping** = objects ↔ database rows
* **Transactions** = framework support
* **Migrations** = schema management in many ORMs
* **Trade-off** = abstraction can hide inefficient queries

---

### 33. What is an ODM?

**ODM = Object-Document Mapper**

* **Object** = application object
* **Document** = NoSQL document
* **Mapper** = connects objects to documents
* **Example** = Mongoose for MongoDB

---

### 34. ORM vs ODM?

**ORM = relational databases, ODM = document databases**

* **ORM** = objects ↔ rows/tables
* **ODM** = objects ↔ documents
* **ORM example** = Hibernate
* **ODM example** = Mongoose

---

### 35. ORM vs writing raw SQL?

**ORM = productivity and abstraction, raw SQL = direct database control**

* **ORM** = faster development
* **Raw SQL** = precise query control
* **ORM** = useful for standard CRUD
* **Raw SQL** = useful for complex/performance-critical queries
* **Production** = often use both

---

### 36. What is the N+1 query problem?

**N+1 = one query followed by N additional queries**

```text
Query users → 1 query
For each user → N queries for orders
Total → N + 1 queries
```

* **Problem** = excessive database calls
* **Cause** = inefficient relationship loading
* **Solution** = joins, eager loading, batching
* **Impact** = high latency + database load

---

# Request Validation

### 37. What is request validation?

**Request validation = checking incoming data before processing it**

* **Required field** = must be present
* **Type** = expected data type
* **Format** = email, UUID, date, etc.
* **Range** = minimum/maximum values
* **Invalid input** = return `4xx` response

---

### 38. Why is request validation important?

**Validation = never trust client input**

* **Security** = reject malicious input
* **Correctness** = prevent invalid data
* **Database** = protect data integrity
* **API contract** = enforce expected structure

---

### 39. Where should validation happen?

**Validation = API boundary + business layer + database constraints**

* **API layer** = basic input validation
* **Service layer** = business rules
* **Database** = data integrity
* **Principle** = don't rely on only one layer

---

### 40. What is schema validation?

**Schema validation = validate data against defined structure**

```json
{
  "name": "Harshit",
  "age": 30
}
```

* **Schema** = expected structure
* **Required** = mandatory fields
* **Type** = expected data type
* **Constraint** = additional rule

---

### 41. What should happen when validation fails?

**Validation failure = reject request with clear client error**

* **Status** = commonly `400 Bad Request`
* **Error code** = machine-readable identifier
* **Message** = human-readable explanation
* **Fields** = identify invalid input

---

### 42. What is input sanitization?

**Sanitization = cleaning or normalizing unsafe input**

* **Input** = untrusted client data
* **Cleaning** = remove/normalize unwanted content
* **Purpose** = reduce security risks
* **Important** = sanitization does not replace validation

---

### 43. Validation vs sanitization?

**Validation = is it acceptable? Sanitization = make input safe/normalized**

* **Validation** = checks correctness
* **Sanitization** = transforms input
* **Example validation** = email must be valid
* **Example sanitization** = normalize whitespace
* **Both** = useful at API boundaries

---

# Production-Level Questions

### 44. How would you design a typical backend request flow?

**Request flow = Router → Middleware → Validation → Controller → Service → Repository → Database**

* **Router** = identifies endpoint
* **Middleware** = common request processing
* **Validation** = checks input
* **Controller** = handles HTTP concerns
* **Service** = business logic
* **Repository** = database access

---

### 45. Where should authentication happen?

**Authentication = middleware/dependency before protected business logic**

```text
Request
  ↓
Authentication
  ↓
Authorization
  ↓
Validation
  ↓
Controller
  ↓
Service
```

* **Authentication** = verify identity
* **Authorization** = verify permission
* **Validation** = verify request data
* **Controller** = process valid request

---

### 46. How would you secure a REST API?

**API security = authentication + authorization + validation + transport security**

* **Authentication** = verify identity
* **Authorization** = verify permissions
* **Validation** = reject invalid input
* **HTTPS** = encrypt communication
* **Rate limiting** = control request frequency
* **Secrets** = never expose credentials

---

### 47. How would you structure a backend application?

**Backend structure = separate HTTP, business, and persistence concerns**

```text
API / Router
     ↓
Middleware
     ↓
Controller
     ↓
Service
     ↓
Repository
     ↓
Database
```

* **Controller** = HTTP concerns
* **Service** = business rules
* **Repository** = persistence
* **Database** = durable state
* **Benefit** = easier testing and maintenance

---

### 48. What makes a backend API production-ready?

**Production API = correctness + security + reliability + scalability**

* **Correctness** = validation + proper status codes
* **Security** = auth + authorization + HTTPS
* **Reliability** = timeouts + retries + idempotency
* **Scalability** = caching + connection pooling
* **Observability** = logs + metrics + traces


