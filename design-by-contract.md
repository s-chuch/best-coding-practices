# Design by Contract

Design by Contract makes the obligations and guarantees of a function or type explicit. The caller meets the preconditions; the implementation guarantees the postconditions; invariants hold for the lifetime of an object.

## Elements

- **Precondition**: What must be true before the call (caller’s responsibility).
- **Postcondition**: What is guaranteed after a successful call (implementation’s responsibility).
- **Invariant**: A condition that is always true for an object between public operations.

## Practices

- Prefer making illegal states unrepresentable with types (sum types, value objects, non-null collections) over runtime checks alone.
- Validate at system boundaries (API edge, user input). Inside the core, rely on types and contracts.
- Use assertions or language contract facilities for internal invariants that should never be violated by correct code.
- Raise exceptions (or return Result types) for expected failure modes that callers must handle.
- Keep contracts stable. Weakening a precondition or strengthening a postcondition can break clients (related to Liskov substitution).
- Document contracts in the function signature, docstring, or type where the language supports it.

## Example

```python
def withdraw(account: Account, amount: Decimal) -> None:
    # Pre: amount > 0 and amount <= account.balance
    if amount <= 0 or amount > account.balance:
        raise ValueError("invalid withdrawal")
    account.balance -= amount
    # Post: account.balance >= 0
    assert account.balance >= 0
```

## When to Use

- Public APIs and module boundaries.
- Complex domain objects with non-trivial invariants.
- Code that is hard to test exhaustively (contracts catch misuse early).

## When to Be Careful

- Performance-critical inner loops (contract checks have a cost; many languages allow disabling them in production).
- Over-specifying trivial functions.

Contracts turn implicit assumptions into checkable statements and make failures easier to diagnose.
