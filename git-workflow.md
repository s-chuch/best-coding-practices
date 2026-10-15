# Git Workflow and Branching Strategies

## Core Practices (All Strategies)

- Small, atomic commits with clear messages (what + why).
- `main` (or `trunk`) should be releasable.
- Protect `main` with CI checks (build, tests, lint, security scans).
- Prefer short-lived branches (hours, not days or weeks).
- Use pull requests for review even on small changes.

## Trunk-Based Development

Everyone integrates into one main branch at least daily. Short-lived feature branches (if any) merge within hours.

**Characteristics**:
- `main` is always deployable.
- Unfinished work is hidden behind feature flags rather than long-lived branches.
- Releases are tags on `main` or continuous deploys.

**Best for**: Continuous delivery, web services, teams with solid automated tests.

**Elite performers** are significantly more likely to use trunk-based development. Long-lived branches increase merge conflict probability non-linearly and slow review.

## GitHub Flow

Simple: feature branch → pull request → merge to `main` → deploy.

**Best for**: Small-to-medium teams, daily-to-weekly deploys, when you want low overhead.

## GitFlow

Uses `main`, `develop`, feature branches, release branches, and hotfix branches.

**Best for**: Versioned software with multiple supported releases and a formal stabilization phase.

**Trade-off**: Higher coordination cost and longer cycle times. Often unnecessary for continuously deployed web applications.

## Decision Guide

| Situation                              | Preferred approach                  |
|----------------------------------------|-------------------------------------|
| Continuous delivery, good tests        | Trunk-based or GitHub Flow          |
| Small team starting out                | GitHub Flow                         |
| Multiple supported product versions    | Trunk-based + release branches      |
| Formal release stabilization needed    | GitFlow (accept the overhead)       |

## Supporting Practices

- Feature flags for incomplete work on `main`.
- Keep CI fast (ideally under ~10 minutes for trunk-based).
- Automate formatting and linting so reviews focus on logic.
- Require status checks before merge.

The goal is frequent integration and fast feedback. Choose the lightest strategy that matches your release model and test maturity.
