# Checklist

### 🧩 1️⃣ Core Backend Mental Models (FOUNDATION)

You must be able to explain:

* [ ] What a **backend system** really does
* [ ] Stateless vs stateful services
* [ ] Sync vs async processing
* [ ] Request/response lifecycle
* [ ] Idempotency
* [ ] Backpressure

If you get this wrong, architecture collapses.

***

### 🌐 2️⃣ Networking & Protocols (VERY IMPORTANT)

Understand **what runs on the wire**:

* [ ] HTTP/1.1 vs HTTP/2 vs HTTP/3
* [ ] REST principles (and when to break them)
* [ ] gRPC basics
* [ ] WebSockets vs SSE
* [ ] DNS basics
* [ ] Load balancing strategies
* [ ] Reverse proxies

Architects think in **packets**, not frameworks.

***

### 🧠 3️⃣ API Design (Contract thinking)

You can design APIs that survive years:

* [ ] REST resource modeling
* [ ] Pagination strategies
* [ ] Filtering & sorting
* [ ] Error models
* [ ] Versioning strategies
* [ ] Backward compatibility
* [ ] OpenAPI / schema-first design

APIs are **contracts**, not code.

***

### 💾 4️⃣ Data Storage Fundamentals (CRITICAL)

Understand **why**, not just how:

#### Relational

* [ ] ACID
* [ ] Indexing
* [ ] Transactions
* [ ] Isolation levels
* [ ] Query planning

#### NoSQL

* [ ] Key-value
* [ ] Document stores
* [ ] Wide-column
* [ ] CAP theorem

#### Concepts

* [ ] Schema design
* [ ] Normalization vs denormalization
* [ ] Read vs write optimization

***

### ⚡ 5️⃣ Caching Strategies

Know **where & why to cache**:

* [ ] In-memory caching
* [ ] HTTP caching
* [ ] CDN caching
* [ ] Cache invalidation strategies
* [ ] Write-through vs write-back
* [ ] TTL tradeoffs

> “There are only two hard problems in CS…” 😉

***

### 🔄 6️⃣ Async Processing & Messaging

Architect-level backend work lives here:

* [ ] Queues vs pub/sub
* [ ] Message brokers (SQS, Kafka, RabbitMQ)
* [ ] Event-driven systems
* [ ] Exactly-once vs at-least-once
* [ ] Idempotent consumers
* [ ] Dead-letter queues

This separates **apps** from **systems**.

***

### 🔐 7️⃣ Security (Backend perspective)

You must understand:

* [ ] Authentication vs authorization
* [ ] JWT vs sessions
* [ ] OAuth 2.0 / OIDC
* [ ] Secrets management
* [ ] Rate limiting
* [ ] Input validation
* [ ] Zero trust basics

Security is architectural, not a library.

***

### 🧪 8️⃣ Reliability & Resilience (VERY IMPORTANT)

Systems fail. Period.

Know:

* [ ] Timeouts
* [ ] Retries (with backoff)
* [ ] Circuit breakers
* [ ] Bulkheads
* [ ] Graceful degradation
* [ ] Health checks
* [ ] SLA / SLO / SLIs

Architects design for failure.

***

### 📈 9️⃣ Observability (You can’t fix what you can’t see)

You must design:

* [ ] Structured logging
* [ ] Metrics
* [ ] Tracing (OpenTelemetry)
* [ ] Correlation IDs
* [ ] Alerting strategies
* [ ] Incident response basics

Logging is not `console.log`.

***

### 🏗️ 🔟 System Architecture Patterns

You should know when to use:

* [ ] Monolith
* [ ] Modular monolith
* [ ] Microservices
* [ ] Event-driven architecture
* [ ] Serverless
* [ ] BFF (Backend for Frontend)
* [ ] CQRS (basic understanding)

Architects choose **tradeoffs**, not trends.

***

### ☁️ 1️⃣1️⃣ Infrastructure & Deployment (REQUIRED)

You don’t need to be DevOps — but you must understand:

* [ ] Containers (Docker)
* [ ] Orchestration basics (Kubernetes)
* [ ] CI/CD pipelines
* [ ] Blue-green / canary deploys
* [ ] Rollbacks
* [ ] Environment separation
* [ ] IaC basics (Terraform)

Architecture ends at production.

***

### 📊 1️⃣2️⃣ Scalability & Performance

Understand scaling deeply:

* [ ] Vertical vs horizontal scaling
* [ ] Stateless services
* [ ] Database scaling strategies
* [ ] Read replicas
* [ ] Sharding (conceptually)
* [ ] Load testing
* [ ] Capacity planning

Scaling is not just “add more servers”.

***

### 🧠 1️⃣3️⃣ Domain & Business Modeling (Architect core skill)

You should learn:

* [ ] Domain-driven design (DDD basics)
* [ ] Bounded contexts
* [ ] Aggregates
* [ ] Event modeling
* [ ] Anti-corruption layers

This is where **architecture meets business**.

***

### 🛠️ 1️⃣4️⃣ Language & Runtime Internals

Not language-specific, but know:

* [ ] Memory management
* [ ] Concurrency models
* [ ] Threading vs async
* [ ] Blocking vs non-blocking IO
* [ ] Garbage collection basics

This affects performance and correctness.
