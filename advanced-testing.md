# Advanced Testing Techniques

Example-based unit tests remain the foundation. These techniques complement them for higher confidence.

## Property-Based Testing

Instead of one concrete example, state a property that must hold for many inputs. The framework generates cases and searches for counterexamples.

Useful properties:
- **Round-trip**: encode then decode returns the original.
- **Idempotence**: applying twice equals applying once.
- **Invariants**: after an operation, a condition still holds.
- **Metamorphic**: related inputs produce related outputs.

Avoid writing a second implementation of the same logic as the "oracle"—shared bugs will pass. Start with a modest number of generated cases; many bugs appear within the first few dozen inputs.

Property-based tests often find more edge cases than hand-written examples, especially around boundaries and combinations you did not enumerate.

## Mutation Testing

Small, systematic changes (mutants) are introduced into the code. A good test suite should fail (kill the mutant). Survivors indicate weak tests.

- Expensive; run on critical modules or on a schedule rather than on every commit.
- Use the score as a signal about test strength, not as a target to game.
- Complements coverage: high coverage with weak assertions still leaves many mutants alive.

## Contract Testing

Verify that a consumer and provider agree on the interface (consumer-driven contracts). Catches breaking changes between services without full end-to-end environments.

## When to Use What

| Technique              | Best for                              |
|------------------------|---------------------------------------|
| Example-based unit     | Specific behaviors and edge cases     |
| Property-based         | Invariants over large input spaces    |
| Mutation               | Assessing test suite strength         |
| Contract               | Service boundaries                    |
| Integration / E2E      | Collaboration and critical journeys   |

Start with solid example-based tests and the pyramid. Add property-based where invariants are clear, mutation testing where confidence in the suite matters most, and contracts at service boundaries.
