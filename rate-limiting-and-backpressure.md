# Rate Limiting and Backpressure

Rate limiting rejects excess traffic at the boundary. Backpressure slows producers when consumers cannot keep up. Use both.

## Rate Limiting

- Apply at the edge (API gateway, public endpoints) to protect internal capacity and ensure fairness.
- Common algorithms: token bucket (allows bursts), leaky bucket (smooths rate), sliding window.
- Return `429 Too Many Requests` with `Retry-After` and rate-limit headers (`X-RateLimit-Limit`, `Remaining`, `Reset`).
- Make limits configurable and observable (rejection rate per key).
- Use a shared store (Redis with atomic scripts) for multi-instance deployments.

## Backpressure

- Bounded queues between stages. An unbounded queue turns a slow consumer into an out-of-memory failure.
- Concurrency limits (bulkheads) per dependency.
- Load shedding of low-priority work under overload.
- In reactive systems, let the consumer signal demand.
- Propagate the slowdown upstream when you control both sides.

## Practices

- Derive limits from measured capacity, not guesses.
- Combine with timeouts, retries (with budget), and circuit breakers.
- Monitor rejection and queue-depth metrics; a sudden spike may indicate abuse or a downstream problem.
- Test under load so you know the system degrades gracefully rather than falling over.

Rate limiting is the hard ceiling. Backpressure keeps internal components from being overwhelmed before that ceiling is reached.
