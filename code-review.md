# Code Review Best Practices

## For Authors

- Keep pull requests small and focused (roughly ≤100 lines is a good target; 1,000 is usually too large). One logical change per PR.
- Write a clear description: first line says *what*, body explains *why* and any trade-offs.
- Automate style (formatters, linters) so reviewers focus on design and logic.
- Respond to comments by improving the code when possible, rather than only explaining in the thread.
- For AI-generated code: same size limits apply. Reviewers should verify intent, tests, security, and that the change matches the request.

## For Reviewers

- Respond within a business day when practical.
- Focus on:
  - Design and placement in the system
  - Correctness and user impact
  - Complexity (could it be simpler?)
  - Tests (are they present and meaningful?)
  - Naming and clarity
  - Comments that explain *why*
  - Security (auth, input validation, secrets, access control)
  - Concurrency safety if applicable
- Comment on the code, not the person. Explain the reasoning.
- Label minor/optional nits.
- Approve when the change improves the codebase, even if not perfect.
- Read the surrounding context when the diff alone is insufficient.

## Team Practices

- Agree on a short written checklist (design, tests, security, complexity) and keep it in the repo.
- Require CI checks (build, tests, lint, security scans) before human review.
- Use CODEOWNERS or similar for sensitive areas.
- Automate what can be automated; reserve human review for judgment.

## AI-Generated Changes

- Treat agent-written PRs with the same rigor.
- Check size and scope first.
- Verify tests match the intended behavior.
- Confirm access control and validation on new entry points.
- Look for unnecessary dependencies or complexity the task did not require.

Small, frequent reviews produce better feedback and faster learning than large, delayed ones.
