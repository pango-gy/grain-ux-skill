# Errors, Edge Cases & Recovery

Open this file when designing or reviewing: error states, empty states, loading states, validation, destructive actions, network failures, permissions, offline behavior, or any state that is not the happy path.

## Contents

- Edges are the product
- Five layers of error handling
- Every error message answers three questions
- Never blame the user
- Validation timing
- Destructive actions: undo > confirm
- Empty states are screens, not errors
- Loading states
- Partial and stale states
- Offline and network-failure states
- Permission-denied states
- Conflict and concurrency
- Anti-patterns
- Quick checklist

## 1. Edges are the product

Most product time is spent in non-happy states. Loading. Empty. Failed. Partial. Offline. Permission-denied. Stale. Saving. Saved. Conflict.

A product is judged less by its happy path than by how it behaves when something goes wrong. Design the failure case *first* — if the failure is dignified, the success will be too.

## 2. Five layers of error handling

Catch issues at the earliest possible layer. Each layer further down is more expensive for the user:

1. **Prevent** — make the error impossible. Disable invalid options, constrain input, design choices that cannot fail.
2. **Validate inline** — flag errors as the user works, with enough context to fix immediately.
3. **Validate on submit** — final check before commit. Slowest of the preventable tier.
4. **Server error** — request failed despite client validation. User has done their part; the system must explain.
5. **Fatal** — unrecoverable state. Last resort. Must tell the user what to do next (contact support, refresh, retry later).

Push every error one layer up if possible. The best error message is the one the user never sees.

## 3. Every error message answers three questions

What happened. Why. What can I do now.

Bad: "Error 403."
Better: "Permission denied."
Right: "You do not have permission to edit this project. Ask the project owner (alex@example.com) to invite you, or [request access](#)."

If you cannot answer "what can I do now," the error message is incomplete. Even "Try again later" or "Contact support" is better than silence — but only when truly nothing else applies.

## 4. Never blame the user

Errors arrive when the user is already frustrated. Compounding the frustration is a product mistake.

- "Email is invalid" → "We could not find an account with that email."
- "Required field" → "Add your name to continue."
- "Invalid input" → "Use letters, numbers, or hyphens only."
- "Wrong password" → "That password did not match. [Reset password.](#)"

Phrase the problem from the system's perspective ("we could not...") and offer a path forward. Avoid "you did X wrong."

A note on security: for credentials, do not reveal which field was wrong ("email or password incorrect," not "email not found"). Generic for security, specific for everything else.

## 5. Validation timing

- **As-you-type**: only for things that need urgent correction (password strength, character limits with hard caps, format mirrors like phone-number masking). Avoid for general input.
- **On blur**: the default. The user finished the field; check now.
- **On submit**: final pass. Highlight every failed field at once, not one at a time. Focus the first failed field.
- **On server response**: for errors only the server can detect (uniqueness, permissions, business rules).

Never validate on first focus. Showing "Required" the moment the user enters a field they just opened teaches them to ignore validation entirely.

## 6. Destructive actions: undo > confirm

Confirmation dialogs are the weakest form of safety. Users learn to dismiss them — the click costs less than reading. The strongest form of safety is undo.

Hierarchy of safety, weakest to strongest:

1. **No safety** — irreversible action with no warning. Never.
2. **Plain confirm** — "Are you sure?" with two buttons. Lowest bar.
3. **Confirm with object name** — "Delete *Q4 Report (2026)*?" Forces the user to identify what they are deleting.
4. **Confirm with typed input** — "Type the project name to delete." For high-stakes, low-frequency actions.
5. **Soft delete with undo** — action happens immediately; user has a window (5–30 seconds) to undo via toast.
6. **Trash/archive with retention** — moved to a recoverable bin for a known period (often 30 days).

Default to soft delete with undo for almost everything. Reserve typed-input confirm for *truly* irreversible, high-blast-radius operations (deleting an organization, dropping a database).

## 7. Empty states are screens, not errors

The first time a user sees a screen, it is empty. This is not a failure — it is the most important version of the screen.

Required parts of an empty state:

- **What this screen will hold** when it has content.
- **Why it is empty** (optional, only if non-obvious — e.g., a filter is hiding everything).
- **The single most likely first action**.
- **Example or template** if the action is non-trivial.

Anti-patterns:
- "No items." (zero help)
- A blank canvas with no instruction.
- An illustration with no text or action.
- "Get started" with no indication of what "started" means.

Different empty states exist for the same screen:

- **First-time empty** — user has never used this. Teach.
- **Cleared empty** — user has used this but has no current items (e.g., inbox zero). Reflect, do not teach.
- **Filtered empty** — items exist but filters hide them. Offer "Clear filters."

## 8. Loading states

The user must always know: *is something happening, and how long*.

- **< 100ms**: no indicator needed; feels instant.
- **100ms – 1s**: brief subtle indicator (button shows spinner, cursor changes). No full-screen blocker.
- **1s – 4s**: explicit indicator with label ("Generating preview...").
- **4s – 10s**: progress estimate or cancellable. "Compressing video — 30 seconds remaining."
- **> 10s**: must be cancellable, and ideally moveable to background ("Continue browsing; we will notify you").

Optimistic UI for actions whose failure is unlikely and recoverable: update the UI immediately, sync in background, roll back with a clear error if the server rejects.

Skeleton screens are better than spinners for content-heavy loads — they hint at the structure that is coming.

## 9. Partial and stale states

Real systems return partial data. Design for it.

- If 80% of data loaded and 20% failed, show what loaded and flag what failed — never show a generic "Error" that throws away the 80%.
- If data is from cache and may be stale, indicate it ("Last synced 5 minutes ago. [Refresh.](#)").
- For pagination/infinite scroll, fail gracefully at the end. Do not silently stop loading.

## 10. Offline and network-failure states

The user's network will fail. Plan for it.

- Detect offline state; surface it persistently (banner, indicator) so the user knows actions may queue or fail.
- Queue actions where possible; sync when reconnected. Show queued state ("Will send when online").
- Never lose user input to a network error. Local draft + retry > "request failed, please try again" with empty form.
- "Retry" must be one tap. Never make the user re-enter data after a network failure.

## 11. Permission-denied states

The user clicked something they cannot do. Tell them why and how to fix it.

- Identify the missing permission specifically ("You need editor access to this folder," not "Access denied").
- Offer the path: request access, switch account, contact the owner.
- For permissions that may change (e.g., free vs paid tier), make the upgrade path visible without being pushy.

## 12. Conflict and concurrency

Two users edited the same thing. Now what.

- Prefer last-write-wins only for very low-stakes data (cursor positions, presence).
- For content (documents, settings, configurations), surface the conflict — show both versions and let the user choose or merge.
- Never silently overwrite a user's work with another's.
- Show real-time presence ("Alex is also editing this") to prevent the conflict before it happens.

## 13. Anti-patterns

- **Toast error that auto-dismisses in 3 seconds.** The user did not read it. Make errors persistent.
- **"Something went wrong."** Vague to the point of useless. Always say what went wrong if you know.
- **Validation errors in red text only.** Color-blind users cannot see the difference. Pair color with icon or label.
- **Disabled buttons with no tooltip.** Either explain why the button is disabled or do not disable it; offer a path instead.
- **Reset form on validation error.** A cardinal sin. Preserve input, focus the first error, scroll if needed.
- **Confirmation that does not name the object.** "Delete?" → "Delete *Q4 Report*?"
- **Modal errors that block the entire app.** Reserve full-screen blockers for truly fatal states.
- **Empty state showing a generic illustration with no instruction.** Pretty does not mean helpful.
- **"Please wait..."** for more than 1 second with no estimate or progress.
- **Error logs in the UI.** Stack traces and error codes are for support tickets, not for users. Show the user something useful; log the stack trace for the developer.

## 14. Tone in error messages

Error tone scales with stakes.

- **Low stakes** (form validation, missing optional field) — neutral, brief. "Add a subject to send."
- **Medium stakes** (failed save, network hiccup) — neutral, action-oriented. "Could not save. [Try again](#)."
- **High stakes** (data loss risk, billing failure) — formal, clear, no humor. "Your payment did not go through. Your subscription will pause on March 5 unless updated."
- **Catastrophic** (account suspension, security event) — formal, specific, with a real human contact.

Never make a joke in an error message. Even a small one. The user is frustrated; humor reads as dismissive.

## 15. Quick checklist

When reviewing edge cases and errors:

- [ ] Have I designed empty, loading, failed, partial, offline, and permission states?
- [ ] Does every error answer *what*, *why*, and *what now*?
- [ ] Is destructive action reversible (soft delete + undo) or, if not, gated by typed-input confirm?
- [ ] Is validation timing correct: on blur, not on first focus?
- [ ] Are loading states honest about duration?
- [ ] Does the system never blame the user?
- [ ] Does retry preserve user input?
- [ ] Is error tone calibrated to stakes — no jokes, no jargon, no error codes?
