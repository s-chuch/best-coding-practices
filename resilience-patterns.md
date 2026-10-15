# Resilience Patterns

Distributed systems fail. Resilience patterns limit the blast radius and allow recovery. They work best together; used alone they can make outages worse.

## Core Patterns

### Timeout
Every external call should have an explicit timeout. An unbounded wait holds threads and connections indefinitely.

### Retry
For transient failures (network blips, brief 503s). Requirements:
- Small budget (e.g., 2–3 attempts).
- Exponential backoff + jitter (avoid synchronized retry storms).
- Only on idempotent operations, or with idempotency keys.
- Do not retry when the failure rate is already high.

### Circuit Breaker
Stops calling a dependency that is consistently failing. States: closed → open (fail fast) → half-open (probe). Prevents cascading overload.

### Bulkhead
Isolates resources (thread pools, connection pools) per dependency so one slow service cannot starve others.

### Fallback
Degraded but useful behavior when the full path fails (cached data marked stale, safe default, queue for later).

## Composition Order

A common safe order:
1. Bulkhead (limit concurrency)
2. Circuit breaker (fail fast if open)
3. Retry (with timeout and backoff)
4. Fallback

Do not retry when the circuit is open. Timeouts make retries safe; without them, retries multiply resource hold time.

## Checklist

- [ ] Every external call has a timeout.
- [ ] Retries have a budget, backoff, and jitter.
- [ ] Retries only on transient, idempotent failures.
- [ ] Circuit breaker on dependencies that can be down for a while.
- [ ] Bulkheads where multiple downstreams share resources.
- [ ] Fallbacks that do not hide critical failures.
- [ ] Observability on retry counts, open circuits, and fallback rates.

Resilience is a system of coordinated limits, not a collection of independent knobs.
