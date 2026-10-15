# Software Delivery Metrics (DORA)

DORA research identifies five metrics that correlate with better organizational performance and team well-being. Speed and stability are not trade-offs for high performers.

## The Five Metrics

1. **Deployment frequency** — How often changes reach production.
2. **Lead time for changes** — Time from commit to production.
3. **Change failure rate** — Percentage of deployments that cause a failure requiring remediation.
4. **Time to restore service** — How long it takes to recover from a failure.
5. **Reliability** (sometimes framed separately) — Meeting reliability targets.

## How to Use Them

- Measure systems, not individuals. Delivery performance is a team and system property.
- Compare a service to its own past, not to other teams.
- Do not turn the metrics into rigid targets (Goodhart’s law). Use them to spot trends and ask questions.
- Start simple: conversations, the DORA Quick Check, or existing pipeline data before building heavy instrumentation.
- Focus on the biggest constraint, not the worst-looking number.
- The highest-leverage practice is usually **smaller batch sizes** (smaller changes move faster and are easier to recover from).

## Improvement Loop

1. Look at system metrics.
2. Discuss with the team what is actually painful (review delays, large PRs, flaky tests, manual steps, etc.).
3. Pick one or two concrete actions.
4. Measure again.

## Supporting Practices

- Working in small batches.
- Continuous integration and automated testing.
- Trunk-based development or short-lived branches.
- Fast feedback loops.
- Observability so failures are detected and diagnosed quickly.

Metrics are a starting point for improvement conversations, not a scoreboard.
