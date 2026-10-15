# Best Coding Practices

A curated collection of best practices for efficient programming, clean code, software development workflows, and performance optimization.

**Start here**:
- [quick-reference.md](quick-reference.md) — one-page checklist of the highest-leverage practices.
- [synthesis-and-tradeoffs.md](synthesis-and-tradeoffs.md) — how the principles conflict, cognitive load, AI as an amplifier, and failure modes of over-application.

## Core Principles

- **KISS (Keep It Simple, Stupid)**: Prefer the simplest solution that works. Avoid unnecessary complexity.
- **DRY (Don't Repeat Yourself)**: Extract repeated logic into reusable functions or modules.
- **YAGNI (You Aren't Gonna Need It)**: Don't build features or abstractions until they're actually needed.
- **Single Responsibility**: Each function, class, or module should do one clear thing.
- **SOLID**: Especially Single Responsibility, Open/Closed, and Dependency Inversion for maintainable design.
- **Clear naming**: Use descriptive names that convey intent. Follow language conventions.
- **Guard clauses / early returns**: Flatten control flow and reduce nesting.

> Always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live.

## Efficient Programming

- Choose appropriate **algorithms and data structures** (understand Big-O).
  - Hash maps/sets for average O(1) lookups.
  - Prefer built-in libraries and language idioms (they're optimized).
- Avoid unnecessary work: early exits, cache results, hoist loop-invariants.
- Vectorize or use bulk operations when dealing with data (e.g., NumPy).
- Write code that is clear for both humans and compilers/interpreters.

## Optimization

Donald Knuth: *"We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3%."*

1. Make it correct and clear first.
2. Profile with realistic workloads to find real bottlenecks.
3. Optimize algorithms and data structures before micro-optimizations.
4. Measure before and after. Keep the change only if the benefit justifies any readability cost.
5. Document non-obvious optimizations.

## Development Workflow

- Version control (Git) with small, atomic commits.
- Code reviews on small pull requests.
- CI/CD with automated tests and checks.
- Linters, formatters, and type checkers.
- Tests as a safety net for refactoring.
- Document *why* (trade-offs, constraints), not just *what*.
- Modular design and observability.

## Guides

- [quick-reference.md](quick-reference.md) — One-page checklist.
- [synthesis-and-tradeoffs.md](synthesis-and-tradeoffs.md) — Trade-offs, cognitive load, AI amplification, and failure modes.
- [principles.md](principles.md) — Expanded explanations of the core principles.
- [clean-code-examples.md](clean-code-examples.md) — Before/after examples of guard clauses, naming, and extraction.
- [modern-practices.md](modern-practices.md) — AI-assisted development, architecture patterns, and CI/CD overview.
- [testing-guide.md](testing-guide.md) — Testing pyramid, unit/integration/E2E, TDD, and anti-patterns.
- [security-checklist.md](security-checklist.md) — OWASP-aligned secure coding checklist.
- [security-patterns.md](security-patterns.md) — Injection, XSS, CSRF, and access-control patterns with defenses.
- [profiling-and-optimization.md](profiling-and-optimization.md) — Profiling tools, measurement process, and optimization guidance.
- [error-handling-and-logging.md](error-handling-and-logging.md) — Exceptions, structured logging, and context.
- [code-review.md](code-review.md) — Practices for authors and reviewers, including AI-generated code.
- [refactoring.md](refactoring.md) — Common techniques and a safe process.
- [concurrency.md](concurrency.md) — Concurrency vs parallelism, models, and safety.
- [database-practices.md](database-practices.md) — Indexing, query habits, and schema guidance.
- [api-design.md](api-design.md) — Resource-oriented REST design, versioning, idempotency, and errors.
- [supply-chain-and-dependencies.md](supply-chain-and-dependencies.md) — Lockfiles, SBOMs, provenance, and continuous monitoring.
- [observability.md](observability.md) — Logs, metrics, traces, and the four golden signals.
- [documentation.md](documentation.md) — READMEs, ADRs, and docs-as-code.
- [caching.md](caching.md) — Layered caching, patterns, and invalidation.
- [architecture-patterns.md](architecture-patterns.md) — Modular monolith, hexagonal/clean, DDD, and when to use them.
- [delivery-metrics.md](delivery-metrics.md) — DORA metrics and how to improve delivery.
- [code-quality-metrics.md](code-quality-metrics.md) — Cyclomatic complexity, maintainability index, and signals.
- [event-driven.md](event-driven.md) — When to use events, outbox, idempotency, and pitfalls.
- [git-workflow.md](git-workflow.md) — Trunk-based, GitHub Flow, GitFlow, and when to use each.
- [feature-flags.md](feature-flags.md) — Types, practices, and cleanup.

## Resources

- *Clean Code* — Robert C. Martin
- *Code Complete* — Steve McConnell
- *Refactoring* — Martin Fowler
- *Domain-Driven Design* — Eric Evans
- Language style guides (PEP 8, Google style guides, etc.)
- Big-O / DSA practice resources
- OWASP Secure Coding Practices Quick Reference Guide
- OpenTelemetry, CycloneDX / SBOM, DORA research

---

Contributions and improvements welcome. Focus on timeless principles over trends.
