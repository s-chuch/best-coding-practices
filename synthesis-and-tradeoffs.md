# Synthesis: Trade-offs, Cognitive Load, and Higher-Order Thinking

The individual guides describe useful practices. This note connects them and surfaces the non-obvious constraints.

## Principles Conflict

DRY, KISS, and YAGNI are not absolute. They pull in different directions:

| Tension              | Naive reading                  | Better reading                                      |
|----------------------|--------------------------------|-----------------------------------------------------|
| DRY vs KISS          | Abstract every duplicate       | Abstract only when it reduces total complexity      |
| DRY vs YAGNI         | Build a reusable framework now | Extract a focused rule; generalize later            |
| KISS vs correctness  | Shorter is better              | Simplest *correct* code is better                   |
| YAGNI vs boundaries  | No structure yet               | Domain, data, and external seams are often current needs |

**Heuristic**: Prefer the design that is easiest to change for the requirements you have evidence for. Cost to add later is low → keep it simple. Same knowledge appears in three places → extract. Domain is volatile → delay abstraction. Domain is stable and shared → introduce a named abstraction with tests.

In an AI-assisted world the cost of later refactoring may fall, which raises the relative weight of YAGNI. Still abstract when the same *business fact* is repeated, not merely when code looks similar.

## Cognitive Load Is the Real Constraint

Working memory holds roughly four chunks. Code is read far more often than it is written. The goal of most style advice is to reduce *extraneous* cognitive load so the reader can spend capacity on the intrinsic difficulty of the problem.

- Deep nesting, unclear names, and distant related logic increase extraneous load.
- Guard clauses, small focused functions, and proximity of related code reduce it.
- Over-abstraction (many shallow modules, layers that do nothing) can increase load even while satisfying surface metrics such as "functions are short."
- Cyclomatic complexity and maintainability index are imperfect proxies; simple size and expert judgment often predict difficulty well.

Write for the next reader’s working memory, not for the checklist.

## AI Amplifies What Already Exists

DORA and related research indicate that AI coding tools act as an amplifier:

- Strong teams (small batches, good tests, review discipline, observability, user focus) get larger gains.
- Weak teams (large changes, weak tests, unclear ownership) can ship faster while accumulating more instability and maintenance cost.

Practical implication: invest in the delivery system (small batches, automated checks, review, observability) before expecting AI volume to improve outcomes. Large AI-generated diffs without those controls increase risk.

## Failure Modes of Over-Applying Practices

- Interfaces and factories with only one implementation.
- Use-case classes that wrap a single line.
- Speculative generality (plugin systems, multi-database support) for requirements that do not exist.
- "Clean architecture" layers that add indirection without protecting a rich domain.
- Feature flags or abstractions that are never removed.
- Treating metrics (coverage, complexity, DORA) as targets rather than signals.

Signs: a change requires touching many files for a small behavior adjustment, or a reader cannot find the actual logic without navigating several layers that add no decision.

## What High-Performing Teams Emphasize

Across DORA and related studies, elite delivery correlates with:

- Small batches and frequent integration (trunk-based or short-lived branches).
- Automated testing and fast feedback.
- Observability and fast recovery.
- Generative culture (cooperation, shared risk, blameless learning).
- User-centric focus so speed creates value rather than just output.
- Leadership that enables the above rather than mandating metrics.

Speed and stability are not trade-offs for the best teams; they reinforce each other when batch size is small and feedback is fast.

## Meta-Principle

Most practices exist to manage two scarce resources: human attention and the cost of change. Prefer designs that:

1. Make the current problem clear to a reader with limited working memory.
2. Keep the cost of the next change low for the requirements you actually have evidence for.
3. Are measured and adjusted when they stop serving those goals.

When a practice starts increasing cognitive load or change cost without a clear benefit, it has become the problem. Revisit it.
