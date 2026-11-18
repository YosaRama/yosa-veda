# Checklist

### 0️⃣ Engineering Fundamentals (Assumed Knowledge)

You must be able to think in **systems**, not features.

* [ ] Testing pyramid (why, not how)
* [ ] Data structures & complexity
* [x] SOLID with real examples
* [ ] Generics & abstraction
* [ ] Basic performance tuning
* [ ] Design Pattern
* [x] Clean Architecture

***

### 1️⃣ System Thinking (CORE of Architecture)

You must be able to think in **systems**, not features.

* [ ] Identify system boundaries
* [ ] Understand inputs / outputs
* [ ] Recognize feedback loops
* [ ] Understand coupling vs cohesion
* [ ] Reason about blast radius
* [ ] Trade local optimization vs global optimization

Architects don’t ask:

> “How do we build this?”

They ask:

> “What happens when this fails?”

***

### 2️⃣ Distributed Systems Fundamentals (CRITICAL)

Modern systems are **distributed by default**.

You must understand:

* [ ] Network failures are normal
* [ ] Latency is unpredictable
* [ ] Partial failure is the default state
* [ ] Time is not synchronized
* [ ] Messages can be duplicated
* [ ] Systems will retry

This mindset changes **everything**.

***

### 3️⃣ Consistency Models (HUGE separator)

You must understand:

* [ ] Strong consistency
* [ ] Eventual consistency
* [ ] Read-after-write
* [ ] Causal consistency
* [ ] CAP theorem (properly, not memes)
* [ ] Tradeoffs between correctness & availability

Architects choose _which inconsistency is acceptable_.

***

### 4️⃣ Data Architecture (Beyond CRUD)

Not “how to query”, but **how data lives**.

* [ ] OLTP vs OLAP
* [ ] Event sourcing (conceptual)
* [ ] Data pipelines
* [ ] Data ownership
* [ ] Data contracts
* [ ] Data retention & deletion
* [ ] GDPR / compliance basics

Data outlives code.

***

### 5️⃣ Cloud Architecture (Vendor-agnostic)

You don’t need to memorize AWS services — but you must understand:

* [ ] Regions vs availability zones
* [ ] Stateless compute
* [ ] Managed services tradeoffs
* [ ] Cost vs scalability
* [ ] Vendor lock-in risks
* [ ] Multi-region strategies (conceptual)

Cloud is **architecture**, not infra magic.

***

### 6️⃣ Cost Engineering (Often ignored, VERY real)

Architects are responsible for **money**.

* [ ] Cost per request
* [ ] Cost per user
* [ ] Fixed vs variable cost
* [ ] Scaling cost curves
* [ ] Caching vs compute tradeoffs
* [ ] When serverless becomes expensive

Good architecture saves **millions**, quietly.

***

### 7️⃣ Security Architecture (Beyond Auth)

Security is a **system property**.

You should understand:

* [ ] Threat modeling
* [ ] Trust boundaries
* [ ] Least privilege
* [ ] Defense in depth
* [ ] Secrets lifecycle
* [ ] Audit logging
* [ ] Incident containment

Security failures are architectural failures.

***

### 8️⃣ Resilience Engineering (REAL WORLD)

Beyond retries & timeouts:

* [ ] Chaos engineering (conceptual)
* [ ] Graceful degradation
* [ ] Feature isolation
* [ ] Fail-open vs fail-closed
* [ ] Disaster recovery planning
* [ ] RTO / RPO

Architects design for **bad days**, not good ones.

***

### 9️⃣ Migration & Evolution (VERY IMPORTANT)

Real systems are **never greenfield**.

You must know:

* [ ] Strangler pattern
* [ ] Incremental refactors
* [ ] Backward compatibility
* [ ] Schema migrations
* [ ] Versioned APIs
* [ ] Decommissioning systems

Most architecture work is **change management**.

***

### 🔟 Decision Making & Tradeoffs (CORE SKILL)

This is what defines an architect.

You must be able to:

* [ ] Compare multiple solutions
* [ ] Articulate tradeoffs
* [ ] Make decisions with incomplete data
* [ ] Explain _why_ a decision was made
* [ ] Revisit decisions without ego

Architecture is **decision records**, not diagrams.

***

### 1️⃣1️⃣ Documentation & Communication

If it’s not understood, it doesn’t exist.

* [ ] Architecture decision records (ADR)
* [ ] System diagrams
* [ ] Clear technical writing
* [ ] Explaining complexity simply
* [ ] Aligning engineers & stakeholders

Great architects **communicate clarity**.

***

### 1️⃣2️⃣ Team & Organizational Design

Systems mirror organizations.

You should understand:

* [ ] Conway’s Law
* [ ] Team boundaries
* [ ] Ownership models
* [ ] Platform vs product teams
* [ ] DevEx as architecture

Bad org design → bad systems.

***

### 1️⃣3️⃣ Product & Business Alignment (VERY SENIOR)

Architects don’t build systems — they enable businesses.

You must learn:

* [ ] Business models
* [ ] Revenue drivers
* [ ] Cost centers
* [ ] Risk tolerance
* [ ] Time-to-market vs correctness
* [ ] Technical debt economics

Architecture exists to serve **business goals**.

***

### 1️⃣4️⃣ Ethics & Responsibility (Often overlooked)

At senior levels, this matters.

* [ ] Data privacy
* [ ] User trust
* [ ] Dark patterns
* [ ] Reliability obligations
* [ ] AI & automation responsibility

You design systems that affect people.
