# Feature Flags

Feature flags (feature toggles) let you deploy code without releasing it to all users. They are a key enabler of trunk-based development and continuous delivery.

## Why Use Them

- Merge incomplete work to `main` safely.
- Decouple deployment from release.
- Progressive rollouts and A/B testing.
- Kill switches for problematic features.
- Reduce long-lived branches and merge conflicts.

## Types

- **Release toggles**: Hide incomplete features. Short-lived. Remove after full rollout.
- **Experiment toggles**: A/B tests. Temporary.
- **Ops toggles**: Circuit breakers or operational controls. May live longer.
- **Permission toggles**: Premium or role-based features. Can be permanent.

## Practices

- Keep the number of active flags manageable. Clean up release flags after rollout.
- Default to off for new features.
- Test both flag states.
- Prefer configuration or a dedicated flag service over scattered `if` statements when the number of flags grows.
- Document the purpose and expected lifetime of each flag.
- Avoid nesting many flags; it recreates complexity.
- Make flag evaluation fast and reliable (do not let a flag service outage take down the application).

## Example

```javascript
if (featureFlags.isEnabled('new-checkout', user)) {
  return newCheckout(cart, user);
}
return legacyCheckout(cart, user);
```

## Cleanup

A flag that stays forever becomes technical debt. Schedule removal once a feature is fully rolled out and stable.

Feature flags are powerful when temporary and disciplined. They become a liability when they accumulate without ownership or removal.
