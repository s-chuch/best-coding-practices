# Error Handling and Logging

## Principles

- **Fail fast and clearly**: A method should either succeed or fail with a useful signal. Do not swallow exceptions silently.
- **Classify errors**: Distinguish recoverable (retry, fallback) from unrecoverable (log and escalate or terminate).
- **Handle at the right level**: Catch only where you can meaningfully recover or add context. Let others propagate.
- **Provide context**: Error messages and logs should answer *what* failed, *on what*, and enough detail to diagnose without reproduction.

## Exception Handling

- Use try/catch/finally (or equivalent) for recovery and resource cleanup.
- Prefer language constructs that guarantee cleanup (e.g., `using`, `with`, try-with-resources).
- Catch specific exceptions before broader ones.
- Do not catch and ignore. At minimum, log.
- Prefer predefined exception types when they fit; create custom ones only when needed.
- For retries: use exponential backoff with jitter to avoid thundering herds.

## Logging Best Practices

- Use a structured logging library that emits JSON (or similar) rather than plain text.
- Include consistent fields: timestamp, level, message, correlation/request ID, user/context IDs, module, and relevant parameters.
- Standard levels:
  - **TRACE/DEBUG**: Detailed developer diagnostics.
  - **INFO**: Normal progress and significant events.
  - **WARN**: Unexpected but non-fatal conditions.
  - **ERROR**: Failures requiring attention.
  - **FATAL**: Critical, process-threatening issues.
- Avoid logging secrets, passwords, tokens, or unnecessary PII.
- Version logs with release SHA or version so incidents can be correlated with deploys.
- Centralize logs (aggregators) and set up actionable alerts. Avoid alert fatigue.
- Sample high-volume success paths; retain full fidelity for errors.

## Observability Tie-in

- Correlate logs with traces and metrics.
- Instrument critical user journeys on both client and server.
- Review error dashboards after deploys.

Clear error handling and useful logs turn production incidents from archaeology into diagnosis.
