# Clean Code Examples

## Guard Clauses / Early Returns

Deep nesting hides the happy path. Invert conditions and return early.

**Before (nested)**:
```javascript
function processPayment(user, amount) {
  if (user) {
    if (user.isActive) {
      if (amount > 0) {
        if (user.balance >= amount) {
          user.balance -= amount;
          return { success: true, newBalance: user.balance };
        } else {
          return { success: false, error: 'Insufficient funds' };
        }
      } else {
        return { success: false, error: 'Invalid amount' };
      }
    } else {
      return { success: false, error: 'Inactive user' };
    }
  } else {
    return { success: false, error: 'User required' };
  }
}
```

**After (guard clauses)**:
```javascript
function processPayment(user, amount) {
  if (!user) return { success: false, error: 'User required' };
  if (!user.isActive) return { success: false, error: 'Inactive user' };
  if (amount <= 0) return { success: false, error: 'Invalid amount' };
  if (user.balance < amount) return { success: false, error: 'Insufficient funds' };

  user.balance -= amount;
  return { success: true, newBalance: user.balance };
}
```

The happy path is now visible at a glance and the function stays flat.

## Meaningful Names

```javascript
// Weak
const d = 86400;
function calc(a, b) { return a * b * 0.1; }

// Clear
const SECONDS_PER_DAY = 86400;
function calculateDiscountedTotal(price, quantity) {
  const DISCOUNT_RATE = 0.1;
  return price * quantity * (1 - DISCOUNT_RATE);
}
```

## Extract Method

When a function does multiple things, extract the named parts.

```javascript
// Before: one long function
function checkout(cart, user) {
  // validate cart
  // calculate totals
  // apply discounts
  // charge payment
  // send confirmation
}

// After: each responsibility named
function checkout(cart, user) {
  validateCart(cart);
  const totals = calculateTotals(cart);
  const finalAmount = applyDiscounts(totals, user);
  const payment = chargePayment(user, finalAmount);
  sendConfirmation(user, payment);
  return payment;
}
```

## Avoid Magic Numbers

```javascript
// Before
if (retries > 3) { ... }

// After
const MAX_RETRIES = 3;
if (retries > MAX_RETRIES) { ... }
```

## Single Responsibility in Practice

A function or class should have one reason to change. If the description needs "and," consider splitting it.

These small, mechanical improvements compound. Apply them consistently and the codebase stays easier to read and change.
