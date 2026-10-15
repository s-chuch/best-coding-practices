# API Design Best Practices

## Resource-Oriented Design

- Use nouns, not verbs: `/orders/{id}` not `/getOrder`.
- Be consistent in naming and hierarchy (`/users/{id}/orders`).
- Prefer plural nouns for collections.
- Keep URLs stable; treat them as a public contract.

## HTTP Methods and Status Codes

- GET for retrieval (safe, idempotent).
- POST for creation (or non-idempotent actions).
- PUT / PATCH for updates (PUT is typically full replacement and idempotent).
- DELETE for removal.
- Use appropriate status codes (200/201/204 success, 400 client error, 401/403 auth, 404 not found, 409 conflict, 429 rate limit, 500 server error).

## Versioning

- Prefer path versioning (`/v1/...`) for external APIs when clarity and cacheability matter.
- Prefer additive changes when possible; introduce a new version only for breaking changes.
- Signal deprecation with headers (Deprecation, Sunset) and a successor link when practical.

## Idempotency and Reliability

- Support idempotency keys on mutating operations so retries are safe (especially important for agents and unreliable networks).
- Design for at-least-once delivery where relevant.

## Errors

- Return machine-readable errors (e.g., RFC 9457 Problem Details style) with type, status, detail, and field-level information.
- Avoid vague prose-only messages.

## Security and Performance

- Always use HTTPS.
- Authenticate and authorize on every request (server-side).
- Rate-limit and validate all inputs.
- Prefer stateless design so instances can scale horizontally.
- Document with OpenAPI (or equivalent) and keep it current.

## Documentation

- Provide clear examples, error formats, and authentication instructions.
- Keep docs in sync with the implementation (generate or validate in CI when possible).

Good APIs are predictable, secure, and easy for both humans and automated clients to use.
