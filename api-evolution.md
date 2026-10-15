# API Evolution and Compatibility

Prefer evolving an API without breaking existing clients. Versioning is the fallback when a change cannot be made additive.

## Non-breaking (usually safe)

- Adding a new endpoint.
- Adding an optional request field or parameter.
- Adding a new response field (clients should ignore unknown fields).
- Adding a new optional header.
- Relaxing a validation constraint.

## Breaking (requires version or coordinated migration)

- Removing or renaming a field, endpoint, or enum value.
- Changing a field’s type, format, or meaning.
- Making an optional field required.
- Tightening validation.
- Changing status-code or error semantics.

## Practices

- Design for extensibility: optional fields, tolerant readers (ignore unknown fields), never repurpose an existing field’s meaning.
- Prefer additive changes. Introduce a new field alongside the old one during a migration window when possible.
- Use semantic versioning for the contract. Reserve major versions for true breaks.
- Signal deprecation with `Deprecation` and `Sunset` headers (and a successor link) before removal.
- Add schema diffing or contract tests in CI to catch accidental breaks.
- Document the compatibility policy for consumers.
- Decouple implementation changes from contract changes (rewriting internals does not require a new version if the contract is unchanged).

## Versioning Styles

- URI (`/v2/...`) — explicit and easy to route.
- Header or media type — cleaner URLs, slightly more client work.
- Query parameter — simple but less common for major versions.

Choose one and document it. The bigger lever is avoiding breaks through additive design.

Compatibility is a product decision. Make it explicit so clients can plan.
