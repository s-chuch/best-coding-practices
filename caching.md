# Caching Strategies

Cache at the outermost practical layer. Design invalidation before you implement the cache. The application must still work when the cache is empty, unavailable, or stale.

## Layers (outer to inner)

1. **Browser / client cache** — Closest to the user. Versioned static assets (long TTL + immutable).
2. **CDN / edge** — Public, relatively static or cacheable responses. Geographic proximity.
3. **API gateway / reverse proxy** — Shared public responses.
4. **Application cache** (Redis, Memcached, in-process) — Shared across instances; user-specific or computed data.
5. **Database** — Internal buffers, materialized views, query results (use carefully).

## What Goes Where

| Data type                  | Typical layer          | Notes                              |
|---------------------------|------------------------|------------------------------------|
| Static assets (JS/CSS/images) | CDN + browser         | Long TTL, content-hashed URLs     |
| Public, slow-changing content | CDN + short app cache | Acceptable staleness               |
| Per-user / private data   | Application cache     | Never CDN; short TTL               |
| Strongly consistent reads | Avoid shared cache    | Or very short TTL + careful invalidation |
| Frequently written data   | Usually not cached    | Write cost often exceeds benefit   |

## Common Patterns

- **Cache-aside (lazy loading)**: Check cache; on miss load from source, store, return. Database remains authoritative. Safest default for most cases.
- **Write-through**: Update cache and source together.
- **Write-behind**: Update cache, asynchronously persist (higher complexity, eventual consistency).
- **Refresh-ahead / warming**: Proactively populate hot keys.

## Invalidation and Safety

- Prefer TTL + explicit invalidation on writes.
- Add jitter to TTLs to avoid stampedes.
- Use locking or request coalescing for popular keys on miss.
- Never cache secrets, auth decisions, or data that must be immediately consistent without a clear strategy.
- Monitor hit ratio, latency, evictions, and stale-data incidents.

## Rules of Thumb

- Start with the 20% of queries that cause 80% of load.
- Public + slow-changing → CDN.
- Private or dynamic → application cache.
- Always have an invalidation or expiry strategy.
- Measure before and after.

Caching is a performance tool, not a correctness tool. Get the consistency model right first.
