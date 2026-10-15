# Code Quality Metrics

Metrics are signals, not goals. Use them to find areas worth human review, not as absolute pass/fail rules.

## Cyclomatic Complexity

Measures independent execution paths (decision points + 1).

| Range   | Interpretation                  |
|---------|---------------------------------|
| 1–5     | Simple, easy to test            |
| 6–10    | Moderate, manageable            |
| 11–20   | Complex; testing becomes harder |
| 21+     | High risk; consider refactoring |

A common guideline is to keep functions under ~10. Higher limits can be acceptable with experienced teams and strong testing, but very high complexity correlates with defects and maintenance cost.

## Maintainability Index

Composite of complexity, size, and Halstead volume. Higher is better (commonly scaled 0–100). Low scores flag modules that may be hard to change.

## Other Useful Signals

- Function and file length (long functions often violate single responsibility).
- Duplication.
- Test coverage (as a signal, not a target).
- Dead code.
- Dependency freshness and vulnerability count.

## How to Apply

- Run static analysis and complexity tools in CI (SonarQube, radon, ESLint plugins, etc.).
- Gate or warn on new code more strictly than legacy code.
- Pair metrics with code review. A low-complexity function can still be wrong; a high-complexity one may be justified.
- Prefer reducing complexity through extraction and clearer structure rather than gaming the numbers.

Metrics help focus attention. Judgment still belongs to the people who understand the domain and the constraints.
