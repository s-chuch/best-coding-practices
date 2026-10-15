# Accessibility (a11y)

Accessible interfaces are usable by more people and often clearer for everyone. Target WCAG 2.1/2.2 Level AA for most public web applications.

## Core Practices

- **Semantic HTML**: Use proper headings (logical hierarchy, no skipped levels), lists, buttons, and landmarks (`nav`, `main`, `aside`). Prefer native elements over divs with click handlers.
- **Labels**: Every form control has an associated visible label (`<label for="...">` or equivalent). Placeholder text is not a label.
- **Alternative text**: Meaningful images have descriptive `alt`. Decorative images use `alt=""` or CSS.
- **Keyboard**: All interactive elements are reachable and operable by keyboard. Visible focus indicators. No keyboard traps.
- **Contrast**: Normal text ≥4.5:1; large text ≥3:1. Do not rely on color alone to convey information.
- **Focus and targets**: Focus is not obscured by sticky elements. Touch targets are large enough (≥24×24 CSS pixels in WCAG 2.2).
- **Language**: Set `lang` on the root element; mark language changes.
- **Motion and media**: Respect reduced-motion preferences. Provide controls for auto-playing audio. Captions for video.

## Development Habits

- Use automated checks (axe, Lighthouse, eslint-plugin-jsx-a11y) in CI as a baseline—they catch many but not all issues.
- Manually test keyboard navigation and a screen reader on critical flows.
- Prefer progressive enhancement and responsive layouts that reflow at high zoom.
- Add ARIA only when native semantics are insufficient; incorrect ARIA is worse than none.

## Checklist (quick)

- [ ] Semantic structure and heading hierarchy
- [ ] Form labels
- [ ] Alt text
- [ ] Keyboard access and visible focus
- [ ] Color contrast and not color-only
- [ ] Page language set
- [ ] Tested with keyboard and screen reader on main journeys

Accessibility is a quality attribute like performance and security. Build it in rather than retrofitting later.
