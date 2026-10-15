# Observability: Logs, Metrics, and Traces

Observability lets you understand a system's internal state from its external outputs. The three pillars answer different questions.

## The Three Pillars

| Pillar   | Answers                          | Strengths                          | Limitations                     |
|----------|----------------------------------|------------------------------------|---------------------------------|
| Metrics  | Is something wrong? How much?    | Cheap, great for alerting & SLOs   | Aggregated; limited "why"     |
| Logs     | What exactly happened?           | Full context for an event          | Volume; hard to search if unstructured |
| Traces   | Where did time/errors go?        | End-to-end request path            | Requires instrumentation & sampling |

They are complementary. Correlate them with a shared trace/request ID.

## Logs

- Structured (JSON) with consistent fields: timestamp, level, service, trace ID, message, relevant context.
- Appropriate levels; sample high-volume success paths.
- Centralize and set retention policies.
- Never log secrets.

## Metrics

- Instrument the four golden signals for services: latency (p50/p95/p99), traffic, errors, saturation.
- Use for dashboards, alerting, and SLOs.
- Keep cardinality under control.

## Traces

- Use distributed tracing (OpenTelemetry is a common vendor-neutral choice).
- Propagate context (W3C Trace Context) across service boundaries.
- Add spans for significant operations (DB, external calls, cache).
- Sample appropriately in high-traffic systems.

## Practical Order

1. Metrics + alerting for known failure modes and SLOs.
2. Structured logs for detail.
3. Distributed traces once you have multiple services and need to follow a request.

## After Deploys

Review error rates and key metrics shortly after releases. Treat deploys as experiments with fast feedback.

Good observability turns "something is wrong" into "here is the specific request and why it failed."
