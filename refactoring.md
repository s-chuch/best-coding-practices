# Refactoring Techniques

Refactoring improves internal structure without changing external behavior. Always have tests (or a safe way to verify) before large refactors.

## Common Techniques

- **Extract Method / Function**: Break long methods into smaller, named pieces. Improves readability and reuse.
- **Rename**: Make names reflect intent. One of the highest-leverage, lowest-risk changes.
- **Extract Class**: Split a class that does too many things (violates SRP).
- **Introduce Parameter Object**: Group related parameters into a single object to simplify signatures.
- **Replace Conditional with Polymorphism**: Turn large switch/if chains on type into polymorphic behavior.
- **Move Method / Field**: Relocate functionality to the class that owns the data it uses.
- **Inline**: Opposite of extract—remove unnecessary indirection when it no longer helps.

## Code Smells Often Addressed

- Long methods / large classes (bloaters)
- Duplicated code
- Feature envy / inappropriate intimacy (couplers)
- Complex conditionals
- Primitive obsession

## Safe Process

1. Ensure tests cover the behavior you intend to preserve.
2. Make small, mechanical steps (many IDEs automate Extract Method, Rename, etc.).
3. Commit frequently so you can revert.
4. Prefer preparatory refactoring before adding new features.
5. For legacy systems, consider the Strangler Fig pattern: gradually replace parts while the old system continues to run.

## With AI Assistants

Mechanical refactors (rename, extract method) are often reliable. Structural changes that alter design or abstractions need human review.

Refactoring is how code stays maintainable as requirements evolve. Do it continuously rather than in large, risky batches.
