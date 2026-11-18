# Clean Architecture

### What Problem It Solves

Clean Architecture exists to **protect business logic from change**.

Frameworks, databases, UI, APIs, and tools **change frequently**. Business rules should not.

The goal is to **control dependencies**, reduce blast radius, and keep the system adaptable over time.

***

### Core Rule (Most Important)

> **Dependencies must always point inward.**

* Business rules know nothing about frameworks
* Use cases know nothing about HTTP, DB, or UI
* Infrastructure depends on abstractions, not the other way around

If this rule is followed, the architecture is clean — regardless of folder names.

***

### Layers (Inside → Outside)

#### 1. Domain

**What it is:**

* Entities
* Value Objects
* Domain rules

**Responsibilities:**

* Pure business logic
* No frameworks
* No IO

**Rules:**

* Zero dependency on other layers

***

#### 2. Use Cases (Application / Services)

**What it is:**

* Application-specific business workflows

**Responsibilities:**

* Orchestrate domain logic
* Define _what the system does_

**Depends on:**

* Domain
* Interfaces (ports)

**Must NOT depend on:**

* HTTP
* DB
* UI

***

#### 3. Ports (Interfaces / Contracts)

**What it is:**

* Repository interfaces
* External service contracts

**Purpose:**

* Define what the application _needs_, not how it is implemented

**Example:**

* `UserRepository`
* `PaymentGateway`

***

#### 4. Adapters (Infrastructure)

**What it is:**

* Prisma repositories
* HTTP clients
* Redis cache
* S3 storage

**Responsibilities:**

* Implement ports
* Handle technical details

**Rule:**

* Can change freely without touching business logic

***

#### 5. Delivery (Controllers / Routes / UI)

**What it is:**

* HTTP controllers
* GraphQL resolvers
* CLI handlers

**Responsibilities:**

* Input validation
* Call use cases
* Map errors & responses

**No business logic here**

***

### How SOLID Fits In

Clean Architecture **uses SOLID**, but they are not the same thing.

| Principle | How It Appears in Clean Architecture    |
| --------- | --------------------------------------- |
| SRP       | Each layer has one reason to change     |
| OCP       | Extend behavior via new adapters        |
| LSP       | Adapters interchangeable via interfaces |
| ISP       | Small, focused repository interfaces    |
| DIP       | Use cases depend on abstractions        |

***

### Dependency Inversion (The Key Enabler)

* High-level modules (use cases) define interfaces
* Low-level modules (DB, API, cache) implement them

This allows:

* DB switch (Prisma → HTTP)
* Add cache (Redis)
* Replace framework

Without changing business logic.

***

### Typical Folder Mapping (Example)

```
/users
  /domain
    User.ts
  /services
    GetUserService.ts
  /repositories
    UserRepository.ts
  /adapters
    PrismaUserAdapters.ts
    CachedUserAdapters.ts
  /controllers
    UserController.ts
  /routes
    user.routes.ts
```

⚠️ Folder names can differ — **dependency direction matters more than structure**.

***

### What Clean Architecture Is NOT

❌ A framework\
❌ A folder structure\
❌ Over‑engineering by default\
❌ Only for big systems

It is a **design discipline**.

***

### When to Use It

✅ Long‑lived systems\
✅ Multiple data sources\
✅ Complex business rules\
✅ Teams & scaling

❌ Small scripts\
❌ One‑off apps

***

### One‑Sentence Summary (Interview‑Ready)

> **Clean Architecture is about structuring systems so business logic is independent from frameworks and infrastructure, enforced through dependency inversion and clear boundaries.**
