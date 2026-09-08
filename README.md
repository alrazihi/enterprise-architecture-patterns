# Enterprise Architecture Patterns

A curated catalog of enterprise architecture patterns, trade-off analyses, and decision records.

## Patterns

### 1. CQRS (Command Query Responsibility Segregation)

**Context:** High-throughput systems where read and write workloads have very different scaling characteristics.

**Trade-offs:**

- Pro: Independent scaling of read and write models
- Pro: Optimized data models per workload
- Con: Increased complexity with two models
- Con: Eventual consistency between models

**Use when:** Write volume is much lower than read volume, or when read/write data models need to diverge.

### 2. Event Sourcing

**Context:** Audit trails, financial systems, or any domain where state transitions matter more than current state.

**Trade-offs:**

- Pro: Complete audit log of all state changes
- Pro: Temporal queries and event replay
- Con: Event schema evolution is hard
- Con: Storage and query complexity

**Use when:** Regulatory compliance, audit requirements, or financial transactions.

### 3. Outbox Pattern

**Context:** Guaranteeing message delivery in distributed systems without dual-write problems.

**Trade-offs:**

- Pro: Exactly-once delivery semantics
- Pro: Decouples database and message broker
- Con: Additional polling or CDC infrastructure
- Con: Slight latency increase

**Use when:** Microservices communicating via async messaging.

### 4. Saga Pattern

**Context:** Distributed transactions that span multiple services without two-phase commit.

**Trade-offs:**

- Pro: No distributed locking required
- Pro: Works with polyglot persistence
- Con: Compensating transactions are complex
- Con: No atomicity across services

**Use when:** Multi-service workflows requiring consistency without 2PC.

### 5. Strangler Fig Pattern

**Context:** Migrating legacy monoliths to microservices incrementally.

**Trade-offs:**

- Pro: Low-risk incremental migration
- Pro: Legacy system stays operational during migration
- Con: Proxy/routing layer adds latency
- Con: Requires careful feature flagging

**Use when:** Modernizing legacy systems with zero downtime requirements.

## Decision Records

See [decisions](decisions/) for architecture decision records (ADRs).

## References

- Microsoft Azure Architecture Center
- Martin Fowler's Enterprise Architecture Patterns
- CNCF Cloud Native Patterns
