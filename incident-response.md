# Incident Response and Postmortems

## During the Incident

- Detect and communicate early.
- Assign a clear incident lead.
- Focus on mitigation and restoration first; investigation can follow.
- Keep a timeline of actions and observations.
- Avoid blame during the live response.

## Blameless Postmortem

After the incident is stable:

1. Build an objective timeline from logs, metrics, and chat.
2. Quantify impact (duration, users, error rate, business effect).
3. Identify contributing factors and systemic causes (5 Whys or similar).
4. Produce specific, owned, dated action items.
5. Share the write-up.

### Language

- Prefer "how did the process allow this" over "who did this."
- Focus on systems, tooling, signals, and procedures.
- State the blameless ground rules at the start of the meeting.

### Template Sections

- Summary
- Timeline
- Impact
- Contributing factors
- Root-cause analysis
- Action items (owner + date)
- Lessons learned

## Practices

- Run postmortems for significant incidents promptly (within a day or two while details are fresh).
- Track action items to completion.
- Look for patterns across incidents.
- Use the findings to improve observability, runbooks, and resilience patterns.

Blameless postmortems convert incidents into lasting improvements instead of repeated failures.
