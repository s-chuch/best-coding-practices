# Documentation Practices

## Self-Documenting Code First

Clear names, small functions, and straightforward structure reduce the need for comments. Comments should explain *why*, not *what*.

## README

The README is the front door. It should answer: "I just cloned this—now what?"

- One-sentence description of what the project does.
- Exact setup and run commands.
- How to run tests.
- Links to deeper docs if they exist.
- Keep it short; move architecture and long explanations elsewhere.

## Architecture Decision Records (ADRs)

Capture significant technical decisions with context and consequences.

Suggested lightweight format:

```markdown
# ADR-NNN: Decision stated as a sentence

- **Status:** Accepted
- **Date:** YYYY-MM-DD

## Context
Forces and constraints.

## Decision
What we chose.

## Consequences
Trade-offs and follow-on effects.

## Alternatives
What else was considered.
```

- One decision per ADR.
- Store them in the repository (e.g., `docs/adrs/`).
- Do not rewrite history; supersede an old ADR with a new one when the decision changes.
- Title should state the decision itself.

## Other Docs

- API documentation: keep in sync (OpenAPI, generated docs).
- Runbooks for operations and incident response.
- Prefer docs-as-code so they are reviewed and versioned with the codebase.

## For AI Assistants

Some teams maintain instruction files (e.g., AGENTS.md) that describe conventions, boundaries, and preferred patterns for coding agents. Keep them accurate and concise.

Documentation that lives with the code and explains decisions stays useful long after the original authors move on.
