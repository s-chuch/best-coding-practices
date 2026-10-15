# Technical Debt Management

Technical debt is the implied cost of future change caused by shortcuts or outdated design. It is managed, not eliminated.

## Principles

- Inventory from the codebase (metrics, queries, static analysis), not from memory.
- Prioritize by *interest* (how much it slows delivery, causes incidents, or creates risk) and by how often the surrounding code changes—not by how ugly it looks.
- Prefer a standing capacity allocation (many teams use ~10–30%) over occasional heroic refactoring sprints.
- Pay down incrementally while delivering features; avoid big-bang rewrites unless the alternative is clearly worse.
- Pair every reduction effort with prevention gates so new debt does not refill the bucket.

## Practical Steps

1. **Discover**: Complexity hotspots, duplication, outdated dependencies, missing tests, known fragile areas.
2. **Score**: Interest (delivery drag, incidents, security) × change frequency.
3. **Allocate**: Fixed budget in the roadmap.
4. **Execute**: Small, tested refactors; automate mechanical fixes (dependency bumps, API migrations).
5. **Prevent**: Linters, complexity gates on new code, dependency scanning, review standards.
6. **Track**: Trend the inventory so progress is visible.

## Types to Distinguish

- Deliberate, short-term shortcuts (document and schedule paydown).
- Accidental complexity from poor design.
- Bit rot (dependencies, platforms, knowledge loss).
- Architecture debt in high-churn areas vs frozen modules (focus on the former).

## With AI Assistance

AI can accelerate mechanical refactors and migrations. It still needs human prioritization, tests, and review. Large generated changes without those controls can increase debt.

Debt management is a continuous portfolio activity. Visibility plus a standing budget beats sporadic cleanup.
