# Common Security Patterns and Defenses

Assume all input is untrusted. Validate on the server. Encode on output. Fail closed.

## Injection (SQL, OS, LDAP, etc.)

**Problem**: Untrusted data is interpreted as code.

**Defense**:
- Use parameterized queries / prepared statements. Never concatenate user input into SQL or shell commands.
- Prefer allowlists over denylists for validation.
- Least privilege for database and OS accounts.

```sql
-- Bad
SELECT * FROM users WHERE id = '" + userId + "';

-- Good (parameterized)
SELECT * FROM users WHERE id = ?;
```

## Cross-Site Scripting (XSS)

**Problem**: Untrusted data is inserted into HTML/JS and executes in the victim's browser (reflected, stored, or DOM-based).

**Defense**:
- Context-aware output encoding (HTML, attribute, JavaScript, URL).
- Use framework auto-escaping; do not bypass it without a documented reason.
- Content-Security-Policy that blocks inline scripts by default.
- `HttpOnly` and `Secure` flags on session cookies.
- Sanitize rich text with a dedicated library (e.g., DOMPurify).

## Cross-Site Request Forgery (CSRF)

**Problem**: An attacker's site triggers a state-changing request using the victim's existing session.

**Defense**:
- CSRF tokens on all state-changing requests.
- `SameSite=Lax` or `Strict` cookies.
- Check `Origin` / `Referer` where appropriate.
- Prefer POST (or safer methods) for mutations; do not rely on GET for state changes.

## Broken Access Control

**Problem**: Users can act on resources they do not own (IDOR) or reach privileged functions.

**Defense**:
- Enforce authorization on every request, server-side.
- Check ownership (e.g., query by both resource ID and user ID).
- Deny by default.
- Test with a second user account and as an unauthenticated stranger.

## Other High-Impact Practices

- Never store secrets in code or client-side bundles.
- Use HTTPS everywhere.
- Rate-limit authentication and expensive endpoints.
- Log security events without leaking secrets.
- Keep dependencies updated and scan them (see supply-chain guide).

These patterns cover the majority of high-severity web vulnerabilities. Combine them with the security checklist and automated scanning.
