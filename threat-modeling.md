# Threat Modeling

Threat modeling systematically identifies what can go wrong with a system so you can prioritize mitigations before or during design.

## STRIDE

A common structured approach. For each component and data flow, consider:

| Category              | Question                                      |
|-----------------------|-----------------------------------------------|
| Spoofing              | Can someone pretend to be a legitimate actor? |
| Tampering             | Can data or code be modified unexpectedly?    |
| Repudiation           | Can an action be denied without proof?        |
| Information disclosure| Can sensitive data leak?                      |
| Denial of service     | Can availability be disrupted?                |
| Elevation of privilege| Can someone gain higher rights?               |

## Process

1. Draw the system (data-flow or architecture diagram). Identify trust boundaries.
2. Walk each element and flow with STRIDE (or another structured method).
3. Record threats, likelihood, impact, and existing or planned mitigations.
4. Prioritize and track mitigations as design or code work.
5. Revisit when the architecture changes.

## Practices

- Do it early, when design changes are cheap.
- Match granularity to risk (simple system → one pass; complex → per element).
- Pair with code review, dependency scanning, and testing; modeling does not replace them.
- Store the model with the architecture docs so it stays current.
- Focus on realistic threats to the assets you care about; exhaustive lists of every possible attack are less useful.

Threat modeling turns security from a checklist into a reasoned view of your specific system.
