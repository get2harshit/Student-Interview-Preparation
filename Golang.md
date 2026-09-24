# Golang — Interview Preparation

### 1. What is Go?

**Go = statically typed language designed for simplicity and concurrency**

* **Statically typed** = types checked at compile time
* **Compiled** = converted to machine code
* **Concurrency** = multiple tasks can progress independently
* **Simple** = small language with fewer abstractions
* **Use** = backend services, APIs, distributed systems

---

### 2. Why is Go popular for backend development?

**Go = simple language + fast execution + built-in concurrency**

* **Compiled** = good runtime performance
* **Goroutines** = lightweight concurrent execution
* **Channels** = communication between goroutines
* **Standard library** = strong networking support
* **Deployment** = commonly produces a single binary

---

### 3. What is a goroutine?

**Goroutine = lightweight concurrent function execution**

```go
go processOrder()
```

* **Goroutine** = function running concurrently
* **Lightweight** = cheaper than OS threads
* **Scheduler** = Go runtime manages execution
* **Use** = concurrent I/O and background work

---

### 4. Goroutine vs OS thread?

**Goroutine = runtime-managed, thread = OS-managed**

* **Goroutine** = lightweight
* **Thread** = heavier OS resource
* **Many goroutines** = can run on fewer threads
* **Scheduler** = maps goroutines onto OS threads

---

### 5. What is a channel in Go?

**Channel = communication mechanism between goroutines**

```go
ch := make(chan int)
```

* **Send** = `ch <- value`
* **Receive** = `value := <-ch`
* **Purpose** = safely exchange data
* **Synchronization** = can coordinate goroutines

---

### 6. Buffered vs unbuffered channel?

**Unbuffered = sender waits for receiver, buffered = limited queue**

* **Unbuffered** = capacity `0`
* **Buffered** = has fixed capacity
* **Unbuffered** = direct synchronization
* **Buffered** = allows temporary accumulation

---

### 7. What is a select statement?

**select = wait on multiple channel operations**

```go
select {
case msg := <-ch1:
    ...
case msg := <-ch2:
    ...
}
```

* **Multiple channels** = monitor simultaneously
* **Ready case** = one operation executes
* **Default** = optional non-blocking behavior
* **Use** = timeouts and concurrent workflows

---

### 8. What is a struct?

**Struct = collection of related fields**

```go
type User struct {
    ID   int
    Name string
}
```

* **Field** = property inside struct
* **Type** = defines data type
* **Use** = represent domain entities
* **Similar to** = class-like data structure

---

### 9. Does Go have classes?

**Go = no traditional classes**

* **Struct** = holds data
* **Methods** = define behavior
* **Interface** = defines behavior contract
* **Composition** = preferred over inheritance

---

### 10. What is a method in Go?

**Method = function associated with a type**

```go
func (u User) GetName() string {
    return u.Name
}
```

* **Receiver** = `u User`
* **Method** = `GetName`
* **Value receiver** = receives copy
* **Pointer receiver** = receives reference to value

---

### 11. Value receiver vs pointer receiver?

**Value receiver = copy, pointer receiver = original value**

* **Value receiver** = doesn't modify original
* **Pointer receiver** = can modify original
* **Pointer** = avoids copying large structs
* **Consistency** = usually keep receiver style consistent

---

### 12. What is an interface in Go?

**Interface = set of method requirements**

```go
type PaymentProcessor interface {
    Pay(amount float64) error
}
```

* **Contract** = defines required behavior
* **Implementation** = type satisfies interface implicitly
* **Decoupling** = separates usage from implementation
* **Testing** = makes mocking easier

---

### 13. How does Go implement interfaces?

**Go = interfaces are implemented implicitly**

```go
type Stripe struct{}

func (Stripe) Pay(amount float64) error {
    return nil
}
```

* **No keyword** = no explicit `implements`
* **Method set** = determines compatibility
* **Stripe** = satisfies `PaymentProcessor`
* **Benefit** = loose coupling

---

### 14. What is a pointer?

**Pointer = variable that stores a memory address**

```go
var p *User
```

* **`*User`** = pointer to User
* **`&user`** = address of user
* **`*p`** = value at address
* **Use** = mutation and avoiding copies

---

### 15. What is nil in Go?

**nil = zero value for certain reference-like types**

* **Pointer** = can be nil
* **Slice** = can be nil
* **Map** = can be nil
* **Channel** = can be nil
* **Interface** = can be nil
* **Important** = dereferencing nil pointer can panic

---

### 16. What is a slice?

**Slice = dynamic view over an underlying array**

```go
users := []string{"A", "B"}
```

* **Length** = number of elements
* **Capacity** = available underlying space
* **Dynamic** = can grow using `append`
* **Common** = preferred over arrays

---

### 17. Array vs slice?

**Array = fixed size, slice = dynamic view**

* **Array** = size is part of type
* **Slice** = flexible length
* **Slice** = internally references array
* **Backend code** = slices are used more commonly

---

### 18. What happens when append exceeds slice capacity?

**append = may allocate a new underlying array**

* **Capacity available** = reuse existing array
* **Capacity exceeded** = allocate new array
* **Elements** = copied to new array
* **Result** = new slice returned

---

### 19. What is a map in Go?

**Map = key-value data structure**

```go
users := map[int]string{
    1: "Harshit",
}
```

* **Key** = unique identifier
* **Value** = associated data
* **Lookup** = average O(1)
* **Concurrent access** = requires synchronization

---

### 20. What is the zero value in Go?

**Zero value = default value assigned to uninitialized variable**

* **int** = `0`
* **string** = `""`
* **bool** = `false`
* **pointer** = `nil`
* **struct** = zero value of each field

---

### 21. How does error handling work in Go?

**Go = explicit error handling using returned errors**

```go
result, err := doSomething()

if err != nil {
    return err
}
```

* **error** = interface representing failure
* **`err != nil`** = error occurred
* **Explicit** = caller handles error
* **Benefit** = failures are visible in code

---

### 22. Why doesn't Go use exceptions?

**Go = uses explicit errors instead of exceptions for normal failures**

* **Error return** = expected failure
* **panic** = unexpected/unrecoverable situation
* **Explicit flow** = easier to see failure handling
* **Trade-off** = more repetitive error checks

---

### 23. What is panic?

**panic = abnormal program state causing stack unwinding**

* **Cause** = unexpected serious failure
* **Effect** = normal execution stops
* **recover** = can intercept panic
* **Use** = exceptional situations, not normal errors

---

### 24. What is defer?

**defer = schedules function execution when current function returns**

```go
defer file.Close()
```

* **Execution** = happens at function exit
* **Use** = cleanup resources
* **Examples** = close file, unlock mutex
* **Benefit** = cleanup stays near resource acquisition

---

### 25. What is `defer` commonly used for?

**defer = reliable resource cleanup**

* **File** = `file.Close()`
* **Mutex** = `mutex.Unlock()`
* **Transaction** = rollback cleanup
* **HTTP response** = close body

---

### 26. What is a mutex?

**Mutex = synchronization mechanism for shared data**

```go
mu.Lock()
defer mu.Unlock()
```

* **Lock** = acquire exclusive access
* **Unlock** = release access
* **Purpose** = prevent concurrent data races
* **Trade-off** = excessive locking reduces concurrency

---

### 27. What is a data race?

**Data race = concurrent access to shared data with unsafe writes**

* **Multiple goroutines** = access same memory
* **At least one write** = involved
* **Synchronization** = required
* **Detection** = Go race detector

---

### 28. What is the Go race detector?

**Race detector = runtime tool for detecting data races**

```bash
go test -race ./...
```

* **Detects** = conflicting concurrent accesses
* **Use** = testing/debugging
* **Overhead** = slower execution
* **Production** = usually not enabled

---

### 29. Mutex vs channel?

**Mutex = protect shared state, channel = communicate between goroutines**

* **Mutex** = shared memory synchronization
* **Channel** = message passing
* **Mutex** = simple shared counter/cache
* **Channel** = worker pipelines
* **Principle** = choose based on data flow

---

### 30. What is a WaitGroup?

**WaitGroup = waits for multiple goroutines to finish**

```go
var wg sync.WaitGroup

wg.Add(2)
go func() {
    defer wg.Done()
}()
wg.Wait()
```

* **Add** = number of goroutines
* **Done** = goroutine completed
* **Wait** = block until counter reaches zero
* **Use** = coordinate concurrent tasks

---

### 31. What is a context in Go?

**Context = carries cancellation, deadlines, and request-scoped values**

```go
ctx, cancel := context.WithTimeout(ctx, time.Second)
defer cancel()
```

* **Cancellation** = stop unnecessary work
* **Deadline** = maximum execution time
* **Request scope** = propagate request information
* **Use** = HTTP/database calls

---

### 32. Why is context important in backend services?

**Context = prevents abandoned work from continuing**

```text
Client
  ↓
API
  ↓
Service
  ↓
Database
```

* **Client disconnects** = request context can cancel
* **Timeout** = downstream work stops
* **Propagation** = pass context through service layers
* **Benefit** = saves resources

---

### 33. What is a goroutine leak?

**Goroutine leak = goroutine remains running unnecessarily**

* **Cause** = blocked channel
* **Cause** = missing cancellation
* **Cause** = infinite loop
* **Impact** = memory/resource consumption
* **Prevention** = context cancellation + proper channel lifecycle

---

### 34. What is Go's garbage collector?

**Garbage Collector = automatically reclaims unreachable memory**

* **Automatic** = developer doesn't manually free memory
* **Heap** = dynamically allocated memory
* **GC** = identifies unreachable objects
* **Trade-off** = consumes CPU and can affect latency

---

### 35. Stack vs heap in Go?

**Stack = function-local execution memory, heap = dynamically retained memory**

* **Stack** = function call data
* **Heap** = values that outlive local scope
* **Escape analysis** = compiler determines allocation location
* **Important** = don't assume every pointer means heap allocation

---

### 36. What is escape analysis?

**Escape analysis = compiler determines whether values can stay on stack**

* **Stack allocation** = cheaper lifecycle
* **Heap allocation** = required when value escapes
* **Compiler** = performs analysis automatically
* **Goal** = optimize memory allocation

---

### 37. What is a package in Go?

**Package = reusable unit of Go code**

* **Package** = groups related functionality
* **Import** = uses another package
* **Exported** = starts with uppercase
* **Unexported** = starts with lowercase

---

### 38. What is a Go module?

**Module = versioned collection of Go packages**

```bash
go mod init my-service
```

* **go.mod** = dependency/module definition
* **Versioning** = tracks dependency versions
* **Dependency management** = handled by Go tooling
* **go.sum** = dependency checksums

---

### 39. What is `go.mod`?

**go.mod = defines module identity and dependencies**

```text
module payment-service

go 1.24

require (
    ...
)
```

* **Module** = project identifier
* **Go version** = language/toolchain version
* **Require** = dependencies
* **Purpose** = reproducible dependency management

---

### 40. What is `go test`?

**go test = Go's built-in testing command**

```bash
go test ./...
```

* **Unit tests** = test individual behavior
* **Table-driven tests** = test multiple cases
* **Benchmark** = measure performance
* **Race** = detect concurrent data races

---

### 41. What is table-driven testing?

**Table-driven testing = test cases stored as data**

```go
tests := []struct {
    input    int
    expected int
}{
    {2, 4},
    {3, 9},
}
```

* **Test case** = input + expected result
* **Loop** = executes cases
* **Benefit** = less repetitive test code
* **Common** = idiomatic Go testing style

---

### 42. How do you build a REST API in Go?

**Go REST API = HTTP router + handlers + service + repository**

```text
Client
  ↓
HTTP Router
  ↓
Handler
  ↓
Service
  ↓
Repository
  ↓
Database
```

* **Router** = maps URL to handler
* **Handler** = handles HTTP concerns
* **Service** = business logic
* **Repository** = database operations

---

### 43. What is the difference between handler and service?

**Handler = HTTP layer, service = business layer**

* **Handler** = request/response handling
* **Service** = business rules
* **Handler** = should stay thin
* **Service** = reusable across interfaces

---

### 44. How do you make a Go API production-ready?

**Production Go service = concurrency + reliability + observability + clean architecture**

* **Context** = cancellation and timeouts
* **Connection pool** = reuse database connections
* **Graceful shutdown** = finish active requests
* **Logging** = structured application events
* **Metrics** = latency, errors, throughput
* **Tracing** = follow requests across services

---

### 45. How do you gracefully shut down a Go service?

**Graceful shutdown = stop accepting new requests and finish existing work**

```text
Signal
  ↓
Stop accepting requests
  ↓
Wait for active requests
  ↓
Close DB/connections
  ↓
Exit
```

* **Signal** = SIGTERM (termination signal)
* **Context** = carries shutdown deadline
* **Timeout** = prevents indefinite waiting
* **Goal** = avoid dropped requests and corrupted work

---

### 46. Why is Go suitable for microservices?

**Go = lightweight deployment + strong networking + concurrency**

* **Binary** = easy container deployment
* **Goroutines** = efficient concurrent requests
* **HTTP/gRPC** = strong networking support
* **Startup** = generally fast
* **Memory** = relatively efficient for many services

---

### 47. What is gRPC in Go?

**gRPC = high-performance RPC framework commonly used with Go**

* **RPC** = remote procedure call
* **Protocol Buffers** = service/data contract
* **HTTP/2** = transport protocol
* **Streaming** = supports bidirectional communication
* **Use** = service-to-service communication

---

### 48. Go concurrency vs parallelism?

**Concurrency = managing multiple tasks, parallelism = executing simultaneously**

* **Concurrency** = structure multiple tasks
* **Parallelism** = tasks execute at same time
* **Goroutines** = enable concurrency
* **Multiple CPU cores** = enable parallel execution
* **Go runtime** = schedules goroutines across threads

---

### 49. How would you handle a CPU-intensive task in Go?

**CPU-intensive work = use parallel workers carefully**

* **Goroutines** = provide concurrency
* **Worker pool** = controls number of workers
* **CPU cores** = determine useful parallelism
* **Queue** = decouples incoming work
* **Important** = don't create unlimited goroutines

---

### 50. How would you design a production Go backend?

**Production Go backend = API + services + persistence + concurrency + observability**

```text
                 Load Balancer
                       ↓
              ┌───────────────┐
              │  Go Services  │
              └───────┬───────┘
                      ↓
               Service Layer
                      ↓
              Repository Layer
                ↙           ↘
           PostgreSQL      Redis
                      ↓
                 Message Queue
                      ↓
                   Workers
```

* **API layer** = HTTP/gRPC communication
* **Service layer** = business logic
* **Repository** = persistence abstraction
* **Redis** = caching/rate limiting
* **Queue** = asynchronous processing
* **Workers** = background processing
* **Observability** = logs, metrics, tracing
