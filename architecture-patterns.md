# Architecture Patterns

Prefer the simplest architecture that meets current needs. Most systems start as a modular monolith. Introduce more sophisticated patterns only when the domain or team size justifies the cost.

## Modular Monolith

Clear domain boundaries inside one deployable unit. Modules communicate through explicit interfaces. Easiest to start with and refactor later into services if needed.

## Hexagonal / Ports and Adapters / Clean Architecture

- Domain logic sits at the center with no infrastructure dependencies.
- Dependencies point inward only: Infrastructure → Application → Domain.
- Ports (interfaces) are defined by the domain; adapters implement them for databases, APIs, UIs, tests.
- Excellent testability and technology independence.
- Overhead is justified when domain logic is rich, long-lived, and must be testable without I/O, or when multiple entry points exist.

Skip or keep light for simple CRUD, prototypes, or small teams.

## Domain-Driven Design (DDD) Building Blocks

Use when the business domain is complex:

- **Entities**: Identity + behavior.
- **Value Objects**: Immutable, equality by value.
- **Aggregates**: Consistency boundary; one repository per aggregate.
- **Domain Events**: Record of something that happened.
- **Repositories**: Persistence abstraction (per aggregate).
- **Application services**: Orchestrate use cases; do not contain core business rules.

Avoid anemic domain models (entities as pure data bags with all logic in services).

## Event-Driven Architecture

Useful when multiple consumers need the same state change, producers and consumers should evolve independently, or latency/scaling profiles differ.

- Prefer at-least-once delivery + idempotent consumers (true exactly-once across the network is not practical).
- Use the transactional outbox pattern for reliable publishing.
- Distinguish thin event notifications from event-carried state transfer.
- Invest early in tracing, idempotency, and dead-letter queues.
- Do not use events when a synchronous response is required.

## Guidance

- Start simple. Evolve only when measured pain or clear future needs appear.
- Document significant choices as ADRs.
- Enforce boundaries (module or package rules, architecture tests) so the design does not erode.

Architecture exists to manage complexity. Extra patterns should reduce complexity more than they add.
