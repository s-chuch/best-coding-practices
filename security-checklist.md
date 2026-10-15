# Secure Coding Checklist

Based on OWASP Secure Coding Practices Quick Reference Guide and OWASP Top 10. Use as a review aid during development and pull requests.

## Input Validation

- [ ] Validate all input on a trusted system (server-side).
- [ ] Classify data sources as trusted vs untrusted.
- [ ] Use a centralized validation routine.
- [ ] Specify and enforce character sets (e.g., UTF-8).
- [ ] Reject invalid input rather than attempting to sanitize in place when possible.
- [ ] Validate after decoding (e.g., UTF-8).

## Output Encoding

- [ ] Encode output on a trusted system.
- [ ] Use context-appropriate encoding (HTML, JavaScript, URL, CSS, etc.).
- [ ] Sanitize data used in SQL, OS commands, LDAP, or XML.
- [ ] Prefer parameterized queries / prepared statements over string concatenation.

## Authentication & Session Management

- [ ] Require authentication for non-public resources.
- [ ] Use well-tested, standard authentication mechanisms.
- [ ] Fail securely (deny by default).
- [ ] Protect session identifiers (secure, HttpOnly, SameSite cookies).
- [ ] Invalidate sessions on logout and after inactivity.
- [ ] Enforce strong password policies and secure storage (hashing with salt + work factor).

## Access Control

- [ ] Enforce authorization on every request, server-side.
- [ ] Use a single, centralized access-control check.
- [ ] Deny by default.
- [ ] Restrict access to sensitive functions, URLs, and files.
- [ ] Avoid relying solely on client-side checks.
- [ ] Test for broken access control (IDOR, privilege escalation).

## Cryptography & Secrets

- [ ] Use strong, standard algorithms and libraries.
- [ ] Never hard-code secrets, keys, or credentials.
- [ ] Rotate secrets and limit their scope.
- [ ] Protect data in transit (TLS) and at rest when required.

## Error Handling & Logging

- [ ] Do not expose sensitive information in error messages.
- [ ] Log security-relevant events without logging secrets or PII unnecessarily.
- [ ] Fail securely and handle exceptions without leaking internals.

## Dependencies & Supply Chain

- [ ] Pin dependencies and use lockfiles.
- [ ] Scan for known vulnerabilities (SCA).
- [ ] Prefer minimal dependency surface.
- [ ] Verify integrity where practical.

## General

- [ ] Apply least privilege.
- [ ] Keep systems and libraries updated.
- [ ] Remove unused code, endpoints, and debug features before production.
- [ ] Run SAST, secret scanning, and dependency checks in CI.

**Note**: Broken Access Control is the top risk in recent OWASP Top 10 lists. Test as different users and as an unauthenticated stranger.
