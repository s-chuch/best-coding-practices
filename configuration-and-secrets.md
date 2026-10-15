# Configuration and Secrets

## Core Rules

- **Never commit secrets** to version control. Once in history, assume compromised.
- Store configuration that varies between environments (hosts, feature flags, log levels) outside the code.
- Distinguish configuration (harmless if leaked) from secrets (grant access).
- Use different credentials per environment. Never share production secrets with dev or test.
- Validate required configuration at startup and fail fast with a clear message.
- Provide a `.env.example` (or equivalent) that lists required variables without real values.

## Twelve-Factor Guidance

Configuration belongs in the environment. The application reads it at runtime. This keeps the same build runnable across environments.

## Local Development

- Use a gitignored `.env` file.
- Commit only the example template.
- Prefer a secrets manager or platform-injected variables even locally when practical.

## Production

- Prefer a dedicated secrets manager (cloud provider, Vault, etc.) over plain environment variables for sensitive values when the platform supports it.
- Environment variables remain common and acceptable when the deployment platform injects them securely and they are not logged or exposed in crash reports.
- Rotate secrets on a schedule and after any suspected exposure.
- Apply least privilege to service accounts and API keys.
- Audit access to secrets where the platform allows.

## Frontend Warning

Anything shipped to the browser is public. Never put secrets in client-side code or frontend environment variables that are bundled.

## Practices

- Scan commits and CI for accidental secrets.
- Document ownership and rotation for each secret.
- Keep configuration typed and validated rather than stringly-typed lookups scattered through the code.

Separation of config from code and rigorous handling of secrets are foundational security and operability practices.
