# Quick Reference Checklist

A one-page reminder of the highest-leverage practices.

## Before Writing Code
- [ ] Understand the problem and constraints.
- [ ] Prefer the simplest solution that works (KISS / YAGNI).

## While Writing
- [ ] Descriptive names.
- [ ] Small functions with one responsibility.
- [ ] Guard clauses / early returns instead of deep nesting.
- [ ] No duplicated logic (DRY).
- [ ] No magic numbers.
- [ ] Parameterized queries and server-side validation.
- [ ] Meaningful error messages and structured logs.

## Before Committing
- [ ] Tests cover the new behavior and edge cases.
- [ ] Linters and formatters pass.
- [ ] No secrets in the code.
- [ ] Commit message explains what and why.

## Pull Request
- [ ] Small and focused (≤ ~100 lines when practical).
- [ ] Description states the change and the reason.
- [ ] CI is green (build, tests, scans).
- [ ] Security-sensitive paths reviewed carefully (auth, input, access control).

## Performance
- [ ] Profile before optimizing.
- [ ] Right algorithm and data structure first.
- [ ] Measure the impact of any change.

## After Release
- [ ] Observability covers the change (logs, metrics, traces).
- [ ] Feature flags cleaned up when no longer needed.
- [ ] Decisions recorded as ADRs when architectural.

## Ongoing
- [ ] Dependencies locked, scanned, and updated.
- [ ] Complexity metrics watched on new code.
- [ ] Small batches and frequent integration.

When in doubt: make it clear, make it correct, then make it fast only where measurement shows it matters.
