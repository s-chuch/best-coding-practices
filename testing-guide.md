# Testing Strategy Guide

## The Testing Pyramid

Aim for a healthy distribution:

| Level              | Rough Target | Characteristics                  | Purpose                          |
|--------------------|--------------|----------------------------------|----------------------------------|
| Unit               | ~70%         | Fast, isolated, no I/O           | Business logic, pure functions   |
| Integration        | ~20%         | Real dependencies (DB, queues)   | Component collaboration          |
| E2E / Acceptance   | ~10%         | Full system or critical paths    | User journeys, regressions       |

Too many slow E2E tests create brittle, expensive feedback loops. Prefer many fast unit tests.

## Unit Tests

- Test one behavior per test.
- Use the **AAA** pattern: Arrange, Act, Assert.
- Prefer testing observable behavior over internal implementation details.
- Keep tests independent and deterministic.
- Name tests clearly (e.g., `should_reject_empty_email`).

## Integration Tests

- Verify interactions between modules or with external systems.
- Use containers (Testcontainers, etc.) for databases and services when practical.
- Avoid over-mocking the system under test.

## E2E Tests

- Cover only critical user paths.
- Keep them stable and as few as possible.
- Prefer API-level checks where a full browser is unnecessary.

## Test-Driven Development (TDD)

1. **Red**: Write a failing test for the next small behavior.
2. **Green**: Write the simplest code that makes it pass.
3. **Refactor**: Improve the code while tests stay green.

Useful for new logic and refactoring safety. Not mandatory for every change.

## Additional Practices

- **Contract testing**: Verify interfaces between services (consumer-driven contracts).
- **Shift-left**: Linters, type checkers, and pre-commit hooks catch issues early.
- **Coverage**: Treat as a signal, not a target. High coverage with weak assertions adds little value.
- **Mutation testing**: Can reveal weak tests.
- Keep the suite fast enough that developers run it frequently.
- Automate in CI so every change is verified.

## Anti-Patterns to Avoid

- Testing private methods directly.
- Over-mocking (tests that break on any refactor).
- Flaky tests that fail intermittently.
- Shared mutable state between tests.
- Ignoring the pyramid and relying mostly on slow E2E tests.
