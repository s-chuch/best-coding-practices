# Database Practices and Query Optimization

## Indexing Basics

- Index columns used in WHERE, JOIN, and ORDER BY clauses for frequent queries.
- **Composite indexes**: Column order matters (leftmost-prefix rule). Put equality filters first, then range filters. More selective columns earlier when all are equality.
- **Covering indexes**: Include all columns the query needs so the engine can avoid table lookups.
- **Partial indexes**: Index only the subset of rows that matter (e.g., `WHERE status = 'active'`).
- Choose index type appropriately (B-tree default for equality/range; GIN for full-text/JSON; BRIN for large append-only data).

## When Not to Index

- Very small tables (sequential scan is often faster).
- Low-cardinality columns unless used in a partial index on the rare value.
- Columns that are updated very frequently (write overhead).

## Query Habits

- Use parameterized queries / prepared statements (security + plan reuse).
- Avoid `SELECT *` when only a few columns are needed.
- Prefer set-based operations over row-by-row processing in application code.
- Use EXPLAIN / query plans to verify indexes are used and costs are reasonable.
- Batch writes when appropriate.

## Schema and Design

- Normalize for integrity; denormalize selectively for read performance when measured.
- Foreign keys help the optimizer and enforce integrity.
- Keep transactions short.
- Monitor slow-query logs and index usage.

## Over-Indexing

Every index slows writes and consumes space. Add indexes based on measured query patterns, not speculation. Review unused indexes periodically.

Measure query plans before and after index changes. The right index on the right columns often yields the largest gains in data-access code.
