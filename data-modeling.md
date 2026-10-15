# Data Modeling

A good schema stores each fact once, enforces integrity, and matches the access patterns you actually have.

## Normalization

Aim for third normal form (3NF) for transactional data:

- **1NF**: Atomic values, no repeating groups.
- **2NF**: No partial dependencies on a composite key.
- **3NF**: No non-key column depends on another non-key column.

This prevents update, insert, and delete anomalies.

## Practices

- Prefer surrogate keys (UUID or sequence) when natural keys can change.
- Declare foreign keys, unique constraints, and NOT NULL where the business rule requires them.
- Name tables and columns consistently and descriptively.
- Model the domain, not the UI screen.

## Denormalization

Duplicate data only when measurement shows that joins are a real bottleneck. Document the copies and how they stay in sync (triggers, application logic, materialized views).

Common cases: read-heavy dashboards, caching computed values, audit history.

## Other Patterns

- Soft deletes + audit columns when you need history.
- JSON columns for truly variable attributes; prefer relational columns for stable structure.
- Separate reporting models (star schema, materialized views) from the transactional model when the workloads differ sharply.

## Process

1. Identify the entities and the facts that must not contradict.
2. Normalize to 3NF.
3. Add constraints.
4. Denormalize only after profiling shows a need.
5. Review when access patterns change.

The schema is a long-lived contract. Get the facts in the right places early.
