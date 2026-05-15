# Accessibility & Inclusive Interaction

Open this file when designing or reviewing: keyboard behavior, focus order, touch targets, color contrast, screen reader labels, motion, responsive layouts, localization, or any UI that assumes a specific body, device, network, language, or context.

## Contents

- Accessibility is not a mode
- Keyboard path is a first-class path
- Labels are contracts
- Touch is not hover
- Color must not carry meaning alone
- Motion must respect the body
- Responsive means the task survives
- Inclusion includes language and context
- Anti-patterns
- Quick checklist

## 1. Accessibility is not a mode

Accessibility is the baseline quality of the interface, not an alternate version. A screen that works only with a mouse, perfect vision, a large display, or a quiet room is unfinished.

The test is simple: can the same task be completed without the preferred path?

- Without a mouse.
- Without color perception.
- Without animation.
- Without a wide screen.
- Without perfect network timing.
- Without hearing or seeing transient feedback.

If the answer is no, the interface has a dependency the user did not consent to.

## 2. Keyboard path is a first-class path

Every interactive element must be reachable, understandable, and operable from the keyboard.

- Focus order follows visual and decision order.
- Focus indicators are visible, not removed for aesthetics.
- Dialogs trap focus while open and restore focus when closed.
- Escape closes dismissible overlays; it never destroys work.
- Custom controls expose the same behavior as native controls.

If a flow cannot be completed with Tab, Shift+Tab, Enter, Space, and Escape, the flow is not complete.

## 3. Labels are contracts

Assistive technology reads structure before style. Visual design can imply relationships; screen readers need those relationships encoded.

- Icon-only buttons need accessible names.
- Form fields need persistent labels, not placeholder-only labels.
- Error text must be programmatically associated with the field it describes.
- Headings describe the structure of the page, not just visual size.
- Links describe their destination; "click here" is not a label.

A user should understand what a control does without seeing its surrounding decoration.

## 4. Touch is not hover

Hover is a preview state, not a discovery mechanism. Touch users, keyboard users, and many assistive technology users do not have hover.

- Do not hide required actions behind hover-only menus.
- Target size must forgive real fingers, not cursor precision.
- Destructive and adjacent actions need spacing, especially on mobile.
- Gestures need visible alternatives. Swipe can be a shortcut, not the only path.
- Long-press is not an obvious primary affordance.

If a feature only appears after hover, treat it as undiscoverable.

## 5. Color must not carry meaning alone

Color is useful, but fragile. Users may be color-blind, in sunlight, on low-quality displays, or using high-contrast settings.

- Pair color with text, icon, shape, or placement.
- Error fields need a label or icon, not only red borders.
- Status chips need words, not only green/yellow/red.
- Charts need labels, patterns, or direct annotation when color separates series.
- Contrast must support reading, especially for secondary text and disabled states.

Disabled controls are especially risky: low contrast plus no explanation makes the path disappear.

## 6. Motion must respect the body

Motion can explain state change, but it can also make people sick or slow them down.

- Use motion to clarify cause and effect, not to decorate every transition.
- Respect `prefers-reduced-motion`.
- Avoid parallax, large zooms, spinning, and repeated pulsing for core flows.
- Do not rely on animation timing to communicate critical information.
- Keep skeleton and shimmer effects subtle.

The interface should still make sense with all animation removed.

## 7. Responsive means the task survives

Responsive design is not just fitting pixels. The user's task, hierarchy, and next action must survive the viewport change.

- Primary action remains visible or predictably placed on small screens.
- Tables become usable views, not horizontal-scroll traps by default.
- Truncated text keeps the distinguishing information.
- Sticky bars do not cover inputs, errors, or submit actions.
- Mobile keyboards should match the input type: email, number, phone, URL, search.

If mobile removes context that desktop users need, mobile is not a smaller version; it is a broken version.

## 8. Inclusion includes language and context

Users differ by language, expertise, culture, age, ability, and stress level. Good UI does not require users to decode an insider's world.

- Avoid idioms, jokes, and metaphors in critical flows.
- Do not assume names, addresses, phone numbers, dates, or currencies follow one country's format.
- Let users correct identity, locale, and accessibility preferences.
- Avoid shame in health, money, education, productivity, or compliance contexts.
- Prefer plain language over cleverness when stakes rise.

The more vulnerable the context, the more literal and respectful the interface must be.

## 9. Anti-patterns

- **No visible focus state.** Keyboard users cannot tell where they are.
- **Placeholder as label.** The label disappears exactly when the user needs it.
- **Color-only status.** Users who cannot distinguish the color lose the meaning.
- **Hover-only controls.** Touch and keyboard users never discover the action.
- **Tiny adjacent actions.** Small destructive buttons beside primary actions create accidental harm.
- **Animation without reduced-motion fallback.** Motion becomes a barrier.
- **Desktop table squeezed onto mobile.** The data exists, but the task does not.

## 10. Quick checklist

When reviewing accessibility and inclusion:

- [ ] Can the primary task be completed with keyboard only?
- [ ] Is focus visible, ordered, trapped, and restored where needed?
- [ ] Do all controls have persistent labels or accessible names?
- [ ] Does any meaning rely on color, motion, hover, or sound alone?
- [ ] Are touch targets large enough and spaced safely?
- [ ] Does the task still make sense on a narrow viewport?
- [ ] Are language, date, name, currency, and address assumptions explicit and respectful?
