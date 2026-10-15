# Capacity Planning

Capacity planning forecasts resource needs so the system stays within acceptable performance and cost as demand grows.

## What to Track

Focus on a small set of actionable metrics:

- CPU, memory, and disk utilization (average and peak).
- Request rate and growth trend.
- Database connection pool and query latency.
- Storage growth.
- Queue depth or in-flight work for async systems.

## Practices

- Collect from existing monitoring; do not build a separate metrics pipeline.
- Look at growth rates over 7, 30, and 90 days. Prefer conservative projections.
- Set headroom targets (for example, keep peak utilization under 70% so spikes and deploys have room).
- Review and adjust regularly; demand changes.
- Model scenarios (traffic spike, dependency slowdown) rather than only the happy path.
- Tie capacity decisions to SLOs: the goal is to meet the reliability target, not to maximize utilization.

## Process

1. Identify the resources that limit the critical path.
2. Establish current usage and growth trend.
3. Project forward with a safety margin.
4. Decide on scaling actions (vertical, horizontal, caching, architectural change) before the limit is reached.
5. Revisit after significant product or traffic changes.

Capacity planning is continuous and lightweight. Overly complex models are less useful than simple, regularly updated projections grounded in real metrics.
