# Event-Driven Architecture

Events help when producers and consumers should evolve and fail independently, when multiple consumers need the same fact, or when latency/scaling profiles differ. They add operational complexity; use them deliberately.

## When It Helps

- Multiple independent consumers of the same state change.
- Need to add consumers without changing the producer.
- Producer and consumer have different scaling or latency needs.
- Load spikes that a broker can absorb.

## When to Avoid

- The caller needs an immediate synchronous response.
- Simple request/response is clearer and sufficient.
- The team is not prepared for eventual consistency, tracing, and failure modes.

## Core Practices

- **At-least-once + idempotent consumers**: True exactly-once delivery across a network is not practical. Design consumers to handle duplicates safely.
- **Transactional outbox**: Write the business change and the event record in the same database transaction; a separate process publishes the event. Avoids dual-write problems.
- **Schema evolution**: Prefer additive changes or use a schema registry. Document contracts (AsyncAPI or equivalent).
- **Tracing and correlation IDs**: Propagate context so a single business action can be followed across services.
- **Dead-letter queues**: Capture messages that cannot be processed for later inspection.
- **Idempotency keys** where appropriate.

## Event Styles

- **Thin event notification**: "Something happened; go look it up."
- **Event-carried state transfer**: Include the relevant data so the consumer does not need an immediate follow-up call.
- Choose based on consistency needs and payload size.

## Operational Basics

- Monitor lag, error rates, and DLQ depth.
- Make the eventual-consistency model visible to users when it matters.
- Start with simple pub/sub. Add event sourcing, CQRS, or sagas only when a concrete problem requires them.

Events decouple systems. They also shift complexity into observability, idempotency, and failure handling. Invest in those early.
