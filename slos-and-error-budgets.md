# SLOs and Error Budgets

Service Level Objectives turn reliability into a shared, measurable contract between engineering and product.

## Definitions

- **SLI** (Service Level Indicator): A quantitative measure of user-facing behavior (availability, latency, successful transactions).
- **SLO**: A target for an SLI over a window (e.g., 99.9% of requests succeed over 30 days).
- **Error budget**: 100% − SLO. The allowed unreliability you can spend on change and risk.

Example: 99.9% availability SLO → 0.1% error budget → ~43 minutes of downtime in a 30-day window.

## Setting Targets

- Base the SLO on what users tolerate, not on current performance or an impressive number.
- Set the internal SLO tighter than any external SLA so you have warning before contractual impact.
- Start with a few critical user journeys (login, checkout, core API). Not every service needs the same rigor.
- Common starting points: 99% (internal tools), 99.9% (most APIs), 99.95%+ (payments, auth).

## Error Budget Policy

Agree behavior in advance:

| Budget remaining | Typical response                          |
|------------------|-------------------------------------------|
| Healthy (>50%)   | Normal feature velocity                   |
| Mid (25–50%)    | Extra caution; include reliability work   |
| Low (<25%)       | Freeze non-critical changes; focus on reliability |
| Exhausted        | Reliability work takes priority           |

## Alerting

Prefer multi-window burn-rate alerts over static thresholds. A high burn rate (e.g., 14.4×) over a short window pages immediately; slower burns open tickets. This catches both sudden and gradual problems.

## Practices

- Document the SLO, SLI, window, and policy in one place owned by the service team.
- Honor the policy when the budget is exhausted, even when inconvenient.
- Review and adjust quarterly based on data and user feedback.
- Combine with observability so you can see what is consuming the budget.

Error budgets make the trade-off between speed and reliability explicit and shared.
