# Chaos Engineering and GameDays

Chaos engineering deliberately injects failures to discover weaknesses before they appear in production. GameDays are scheduled team exercises that practice incident response under controlled failure.

## Principles

- Start small. Minimize blast radius (one instance, one dependency, staging first).
- Have a hypothesis: "When X fails, the system should Y."
- Observe the full path (retries, timeouts, fallbacks, alerts, human response).
- Stop the experiment if customer impact exceeds the plan.
- Run blameless postmortems and turn findings into concrete improvements.

## GameDay Structure (typical 2–4 hours)

1. Kickoff and roles (Game Master, participants, observers).
2. Failure injection.
3. System restoration.
4. Hot debrief.
5. Action items and documentation.

## What to Exercise

- Dependency failure (database, external API, cache).
- Resource exhaustion (CPU, connections, disk).
- Network partitions or latency.
- Deployment or configuration errors.
- Human process: paging, runbooks, communication.

## Practices

- Prefer staging or a limited production slice until the team is mature.
- Document the experiment, expected behavior, and abort criteria beforehand.
- Ensure monitoring and alerting are visible to everyone during the exercise.
- Capture gaps in observability or runbooks as the primary output.
- Schedule regularly; resilience skills decay without practice.

Chaos engineering validates that resilience patterns (timeouts, retries, circuit breakers, bulkheads) and operational processes actually work under failure.
