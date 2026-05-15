---
name: grain
description: Use when working on any user-facing interface decision — UI components, user flows, forms, input, error states, empty states, copy, microcopy, button labels, navigation, onboarding, dashboards, accessibility, permissions, consent, AI output, automation, billing, sharing, or any moment the user will see, read, click, trust, or recover from something. Covers information architecture, cognitive load reduction, forms and input, accessibility and inclusive interaction, trust and user agency, error prevention and recovery, and microcopy and tone. Applies during design review, code review of UI, writing new components, refactoring flows, drafting product copy, or critiquing screenshots. Not for backend-only logic, infra, or non-user-facing work.
license: MIT
metadata:
  author: "Pango Gy CTO 유승재 <pinkyooysj@pango-gy.com>"
  organization: "Pango Gy"
  homepage: "https://pango-gy.com"
  version: "0.3.0"
---

# grain

A UX philosophy skill. Work with the grain of how people actually think, read, and recover — not against it.

## Setup

When this skill is active, treat every user-facing decision as a UX decision. Apply the **Core laws** to every change. When a decision is non-trivial in a specific domain, open the matching file under `references/` before answering. Call laws and anti-patterns by name (e.g., "this violates *Make the next action obvious*") so reviews stay concrete.

Do not invent rules. If a situation is not covered here, prefer the smallest change that satisfies the laws, and say so.

## Core laws

These cut across every domain. Apply them in order — earlier laws beat later ones when they conflict.

1. **Make the next action obvious.** A user should never have to ask "what do I do now?"
2. **Simplify the rule before the screen.** A complex policy, pricing rule, eligibility rule, or workflow will feel complex no matter how polished the UI is.
3. **Reduce decisions before reducing clicks.** One extra click on a clear path beats one fewer click on a confusing one.
4. **Show state, not just controls.** The user must know what the system is doing, what it just did, and what will happen if they act.
5. **Show value before asking for effort.** Before signup, permission, payment, sensitive input, or a long form, make the benefit and consequence visible.
6. **Usable means accessible.** A flow that depends on perfect vision, a mouse, hover, motion, a large screen, or a fast network is unfinished.
7. **Preserve user effort.** Input, choices, progress, drafts, and context must survive errors, navigation, refresh, and retry.
8. **Let users undo, not just confirm.** Confirmation dialogs train users to ignore them. Reversibility is the real safety net.
9. **Words are UI. Read them aloud.** If a label, error, or instruction sounds awkward spoken, it is wrong. Rewrite.
10. **Match the user's model, not the system's.** Name things after what the user is trying to do, not after the table, endpoint, or class.
11. **Defaults are decisions.** Whatever is pre-selected, pre-filled, or pre-checked, you are choosing for the majority of users. Choose deliberately.
12. **Do not surprise the user.** Sharing, deletion, billing, permissions, AI output, and automation must expose consequences before action.
13. **Edges are the product.** Empty, loading, failed, partial, offline, permission-denied, and conflict states are first-class screens.
14. **Consistency over cleverness.** A novel pattern must earn its place by being demonstrably better; otherwise, match what the rest of the product does.
15. **Respect the user's attention.** Every interruption — modal, toast, badge, sound, vibration — is a withdrawal from a finite budget.

## Domains

### User flow & information architecture

Design the path before the page. A flow is a sequence of decisions; the screen exists to support one decision at a time.

- One primary action per screen. Secondary actions are visually quieter, not just smaller.
- Simplify the policy or eligibility rule before explaining a complicated path.
- Group by the user's task, not by the data model. "Things I own" is a task; "Resources" is a table name.
- Surface the next step inside the current context — do not send users back to a hub to continue.
- Never hide a required step behind a non-obvious affordance (icon-only buttons, hover-only menus, gestures without hints).
- Depth costs more than breadth. A flat 7-item menu beats a 3-level tree of 3 each.
- Entry and exit points must be symmetric: every flow has a clear way out that does not destroy work.

Full reference: [`references/flow-and-ia.md`](references/flow-and-ia.md)

### Cognitive load & simplicity

"Simple" does not mean "few features." It means "few decisions per moment." Hide complexity in time and space, not under the rug.

- Show only what the user needs *to make the current decision*. Move the rest behind progressive disclosure.
- Make every question easy to answer: split hard questions, recommend safe defaults, and retrieve known data.
- Chunk long forms into stages with visible progress. Each stage should be answerable in under 30 seconds.
- Prefer recognition over recall — show options instead of asking users to remember them.
- Reuse the same control for the same idea everywhere in the product. A "Save" button must always save and never sometimes-submit.
- Number of choices is more taxing than length of text. Cutting two options helps more than cutting two sentences.
- Defaults handle the 80% case. Settings handle the 20%. Never make the 80% configure to get the obvious behavior.

Full reference: [`references/cognitive-load.md`](references/cognitive-load.md)

### Forms & input

Input is work. Every field asks the user to spend attention, memory, trust, or private information.

- Ask only what is needed for the next decision or outcome.
- Show why the input is worth giving before asking for sensitive, private, or high-effort data.
- Order fields by the user's reasoning, not by database shape.
- Mark required, optional, and format rules before failure.
- Match control type to data: choose, autocomplete, mask, upload, or free text deliberately.
- Preserve input across errors, navigation, refresh, and network failure.
- Preview imports and bulk changes before mutating durable data.

Full reference: [`references/forms-and-input.md`](references/forms-and-input.md)

### Accessibility & inclusive interaction

Accessibility is not a mode. A screen that works only with a mouse, perfect vision, a large display, or a quiet room is unfinished.

- Every primary task must have a keyboard path.
- Focus order follows decision order; focus indicators remain visible.
- Controls need persistent labels or accessible names.
- Color, motion, hover, and sound cannot carry meaning alone.
- Touch targets must forgive real fingers, especially near destructive actions.
- Responsive design means the task survives the viewport change.

Full reference: [`references/accessibility-and-inclusion.md`](references/accessibility-and-inclusion.md)

### Trust, consent & agency

Users should never wonder, "Wait, did it just send, charge, delete, share, publish, or automate that?"

- Consent must be specific, timely, separable, and revocable where possible.
- Preview before external impact: send, publish, share, import, sync, or bulk edit.
- Automation must show pending, running, completed, failed, skipped, and cancelled states.
- AI output is a draft until the user accepts it.
- Billing, permissions, and privacy copy must expose real consequences.
- Cost, limits, and trade-offs must be visible before conversion pressure appears.
- Durable or shared actions need history: who or what changed what, and when.

Full reference: [`references/trust-and-agency.md`](references/trust-and-agency.md)

### Errors, edge cases & recovery

Errors are the most-read copy in your product. They appear when users are already frustrated — design them first, not last.

- Prevent before validate, validate before submit, submit before fail. Catch issues at the earliest possible step.
- Every error message must answer three questions: *what happened*, *why*, and *what can I do now*.
- Never blame the user. "Email is invalid" → "We could not find an account with that email."
- Make destructive actions reversible by default. Confirmation dialogs are the weakest form of safety; undo is the strongest.
- Empty, loading, partial, offline, and permission-denied states are screens, not afterthoughts. Design them with the same care as the happy path.
- Before improving a loading state, ask whether the wait can be removed, backgrounded, cached, or shortened.
- Measure the user-visible bottleneck before trading readability for optimization.
- Retry must be one tap away. Never make the user re-enter data after a network failure.

Full reference: [`references/errors-and-recovery.md`](references/errors-and-recovery.md)

### Microcopy & tone

Copy is the highest-leverage UI surface — a one-word change in a button label can shift conversion more than a redesign.

- Button labels describe the *result of the action*, not the action itself. "Send invite" beats "Submit." "Delete account" beats "OK."
- Cut every word that does not change the meaning. "Please click here to..." → the verb.
- Match the user's vocabulary, not the team's. If users say "post," do not call it a "submission."
- Sentence case for everything except proper nouns. Title Case Makes Buttons Feel Like Headings.
- Tone scales with stakes. Casual for routine, neutral for transactional, formal for irreversible or legal.
- Respect beats conversion pressure: do not hide cost, effort, risk, or limits behind friendly copy.
- Never write copy you would not read aloud to a stranger.

Full reference: [`references/microcopy-and-tone.md`](references/microcopy-and-tone.md)

## Anti-patterns

Refuse these. If asked to implement one, name the anti-pattern, explain the cost, and propose the smallest alternative that meets the same goal.

1. **Modal as the first thought.** Modals interrupt. Use them only for decisions that block the next step. Never for confirmations of low-stakes actions, never for marketing.
2. **Irreversible destructive action without object-specific safety.** If there is no undo, trash, or retention path, name the object and consequence; for high-blast-radius actions, require typed confirmation.
3. **Error toast that auto-dismisses.** If it disappears in 3 seconds, the user did not read it. Make errors persistent until dismissed or resolved.
4. **Disabled buttons with no explanation.** A greyed-out "Save" with no tooltip teaches the user nothing. Either say why or do not disable it.
5. **Empty state that just says "No items."** Every empty state is a chance to teach what this screen does and offer the first action.
6. **Required field marked only with red text after submit.** Mark required fields *before* the user types, not after.
7. **Loading spinner with no context.** "Loading..." for more than 1 second needs a label ("Generating preview..."). For more than 4 seconds, a progress estimate or a way to cancel.
8. **Hover-only affordances on touch surfaces.** If a feature is only discoverable via hover, it does not exist for half the users.
9. **Settings that hide important behavior.** If toggling a setting could surprise the user later (notifications, sharing, deletion), surface the consequence inline at the moment of toggle.
10. **Onboarding that asks for everything up front.** Ask for what is needed to complete the *next* step, not the entire profile.
11. **Confirmation that does not name the object.** "Are you sure?" → "Delete *Q4 Report (2026)*?"
12. **Success states that vanish.** A success toast that fades before the user looks up leaves them wondering if anything happened. Pair feedback with a persistent state change.
13. **Pointer-only path.** Any task that requires hover, drag, or precise cursor movement must also have a visible keyboard/touch path.
14. **Form that destroys input.** Resetting fields after validation, navigation, refresh, or network failure violates *Preserve user effort*.
15. **Consent bundled into one checkbox.** Required agreement, marketing consent, tracking consent, and data sharing must not be hidden behind one control.
16. **AI or automation that commits without review.** Generated or automated output must not send, publish, charge, delete, or change durable data without explicit approval when stakes are real.
17. **Complex policy disguised as simple UI.** If the underlying rule is confusing, another tooltip or wizard step will not make the product feel simple. Simplify the rule or expose the trade-off honestly.
18. **Asking before value is visible.** Signup walls, permission prompts, payment forms, and sensitive questions must not appear before the user understands why the effort is worth it.
19. **One hard question instead of several easy ones.** If the user must calculate, remember, compare, or infer too much, split the question or let the system do the work.
20. **Spinner as strategy.** A pretty spinner is not a solution when the wait can be removed, backgrounded, cached, or made cancellable.
21. **Unmeasured optimization.** Do not make code harder to read for a theoretical speedup. If the bottleneck is not user-visible or measurable, leave the simpler code alone.

## How to apply

- When reviewing, name the law or anti-pattern by phrase. Generic critique ("this feels off") teaches nothing.
- Suggest the *smallest* change that satisfies the rule. Refactors are expensive; rules are cheap to apply incrementally.
- Preserve the user's voice and product personality. These laws shape *structure*, not personality.
- If two laws conflict in a specific case, prefer the earlier law in the **Core laws** list. Explain the trade-off.
- When unsure, design the failure case first. If the failure is dignified, the success will be too.
- Before implementation or review, identify: the user, the current primary decision, the next action, the failure state, and whether the path still works with keyboard, touch, narrow viewport, and reduced motion.
- Also identify the rule, policy, or business constraint creating the UX cost. If the rule can be simplified, fix the rule before polishing the interface around it.
- Before a flow asks for effort, identify the visible value the user has already received or is about to receive.
- If performance is part of the UX cost, identify the user-visible symptom and the measurement before proposing an optimization.
- For UI code reviews, check changed behavior, not only changed pixels: focus, loading, empty, failed, disabled, permission-denied, undo, and success states.
- For forms, imports, AI, automation, sharing, billing, or destructive actions, open the relevant reference before answering.

## Lineage

These ideas have lineage. Recorded here, in one place, rather than scattered through the text:

- **Donald Norman** — visibility, feedback, mapping, affordance, and the gulf between user intent and system response. (*The Design of Everyday Things*)
- **Jakob Nielsen** — the ten usability heuristics. *Visibility of system status*, *match between system and the real world*, *error prevention*, *recognition over recall*, and *help users recognize, diagnose, and recover from errors* are load-bearing for this skill.
- **Steve Krug** — *Don't make me think.* Scannability, convention over invention, the cost of a misplaced click.
- **Bruce Tognazzini** — First principles of interaction design; the case for reversibility, latency budgets, and Fitts's law in practice.
- **Alan Cooper** — goal-directed design; the distinction between what the system does and what the user is trying to achieve.
- **Dan Saffer** — microinteractions as the texture of a product; the principle that small details are the product.
- **Edward Tufte** — data-ink ratio applied to UI: every pixel either serves the user's task or interferes with it.
