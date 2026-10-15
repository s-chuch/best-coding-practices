# Modern Practices (2025–2026)

## AI-Assisted Development

AI coding assistants and agents (GitHub Copilot, Claude Code, Cursor, etc.) are now widely used. Surveys show high adoption, but trust remains limited (~33% fully trust accuracy). Key practices:

- **Human remains accountable**: Architecture, trade-offs, security, and final merges stay with humans.
- **Spec-driven development**: Give agents clear specifications, acceptance criteria, and bounded context. Avoid pure "vibe coding" for production.
- **Small, reviewable changes**: Prefer agents that open PRs with small diffs. Label AI-generated changes for traceability.
- **Governance**: Approved tools, zero-retention/private endpoints for sensitive code, automated security scanning on every change, and measurement of end-to-end delivery (not just lines generated).
- **Maintenance bottleneck**: Generation is fast; review, testing, and long-term maintainability are the constraints. Enforce complexity budgets and ownership.

Measure productivity by reliable software delivered, not token volume or lines of code.

## Testing Strategy

Follow the **testing pyramid** (or adapted variants):

- **~70% unit tests**: Fast, isolated, cheap. Use AAA (Arrange-Act-Assert). Prefer behavior over implementation details.
- **~20% integration tests**: Verify interactions (DB, services). Use containers (Testcontainers) where practical.
- **~10% E2E / acceptance tests**: Critical user paths only. Keep them few and stable.

**TDD cycle** (where it fits): Red → Green → Refactor. Write the failing test first for new behavior.

Additional practices:
- Contract testing for service boundaries.
- Mutation testing or coverage as signals, not goals.
- Shift-left: linters, type checkers, and pre-commit hooks.
- Keep the suite fast enough for the CI feedback loop.

## Profiling and Performance

Profile before optimizing (Knuth’s critical 3%).

Common tools:
- **Python**: cProfile, line_profiler, Scalene, Pyinstrument, perf (Linux).
- **JVM**: JVisualVM, async-profiler, YourKit, JProfiler.
- **Native / C++**: perf, Valgrind (Memcheck/Massif), gprof, Intel VTune.
- **General**: Flame graphs, continuous profilers (Pyroscope, Grafana, cloud profilers).

Best practices:
- Profile optimized builds (-O2/-O3), not debug.
- Establish baselines and compare before/after.
- Prefer low-overhead sampling in production (perf, eBPF).
- Top-down: system metrics → hotspots → specific code.
- Focus on the Pareto 80/20 (or 90/10) of runtime.

## Secure Coding (OWASP-aligned)

Key areas from OWASP Secure Coding Practices:

- Input validation on the server (trusted system); reject invalid input.
- Output encoding appropriate to context (HTML, SQL, OS commands).
- Strong authentication, session management, and access control (fail securely; enforce on every request).
- Least privilege; protect secrets (never in client code).
- Parameterized queries / prepared statements (never concatenate).
- Secure error handling and logging (no sensitive data in logs).
- Dependency scanning, SBOMs, and supply-chain checks.
- Broken Access Control remains the top risk (OWASP Top 10).

Shift security left: SAST, SCA, and secret scanning in CI.

## Architecture and Modularity

- Prefer **modular monolith** for most new systems: clear domain boundaries inside one deployable unit. Extract services only when scaling or organizational needs justify it.
- High cohesion, low coupling. Communicate through explicit interfaces.
- Single Responsibility at module level.
- Layered or hexagonal architecture for separation of concerns when useful.
- Design for change: boundaries that allow future extraction without full rewrite.

## CI/CD and Observability

- Automated pipelines on every change (build, test, scan, deploy).
- Small batch sizes and trunk-based development where practical.
- Structured logging, metrics, and tracing for production observability.
- DORA-style metrics: deployment frequency, lead time, change failure rate, recovery time.

---

These practices complement the timeless principles in the README and principles.md. Update as tools and evidence evolve.
