# Flow & Information Architecture

Open this file when designing or reviewing: page hierarchy, navigation, multi-step flows, entry/exit paths, dashboards, or any decision about *where* a feature lives.

## Contents

- The path is the product
- Simple policy before simple UI
- One primary action per screen
- Group by task, not by data model
- Depth costs more than breadth
- Entry and exit must be symmetric
- Surface the next step in context
- Pages vs panels vs modals
- Dashboards: rank by decision, not by volume
- Search vs browse vs filter
- Onboarding is the first flow
- Empty states are entry points
- Navigation should orient the user
- Anti-patterns
- Quick checklist

## 1. The path is the product

Before designing a screen, draw the *flow*. A flow is a sequence of decisions; each screen exists to support exactly one of them. If you cannot describe what decision a screen helps the user make in one sentence, the screen has no reason to exist yet.

- Before polishing a branchy flow, ask whether the underlying rule can be simpler. Eligibility rules, pricing tiers, approval policies, and setup requirements are UX. A clear screen wrapped around a confusing rule still feels confusing.
- Sketch the happy path as a line of nodes. Each node is one decision.
- Mark every node where the user could (a) drop out, (b) be blocked, (c) be confused. These are your real design problems — the screens between them are mostly layout.
- Reduce the number of nodes before you optimize any single one.

Simple policy beats explanatory UI. If a flow needs three help paragraphs to explain who qualifies, when it applies, or what happens next, the first design proposal should be a simpler rule.

## 2. One primary action per screen

A screen has at most one primary action. Everything else is secondary.

- Each screen also needs one core message. If the user remembers only one thing from the screen, decide what that should be before arranging components.
- Primary action is visually the heaviest element — filled button, high contrast, anchored where the eye lands.
- Secondary actions are quieter: outline, ghost, or text link. Quieter, not smaller — small primary buttons get missed.
- If you find yourself with two primary actions, you have two screens fighting to live in the same place. Split or rank them.

Examples:
- A signup screen's primary action is "Create account." "Log in instead" is a text link, not a second button.
- A document editor's primary action shifts by mode — "Save" while editing, "Publish" once saved, "Share" once published.

## 3. Group by task, not by data model

Users do not think in tables. They think in tasks.

- "Things I own," "Things shared with me," "Things I am waiting on" are tasks.
- "Resources," "Entities," "Records" are tables.
- The IA mirrors the user's mental model of the work, not the database schema. If a single user task spans three tables, the IA should still put that task on one screen.

When in doubt, write down the sentence the user would say to a coworker: *"I'm trying to find the proposals I sent last week."* The IA should make that sentence trivial to execute.

## 4. Depth costs more than breadth

A flat menu of 7 items is faster than a tree of 3×3 items. Every level of depth doubles the cost: the user must remember where they came from and predict where they are going.

- Cap navigation depth at 2 levels for most products. 3 only with strong reason.
- Hub-and-spoke beats nested when the user moves between siblings frequently.
- If you must go deep, make breadcrumbs persistent and clickable at every level.

Breadcrumbs are a depth bandage, not a depth solution. If users *need* breadcrumbs to feel oriented, the IA is too deep.

## 5. Entry and exit must be symmetric

For every entry into a flow, there must be a clear, non-destructive way out.

- A "Cancel" or "Back" that preserves entered data is mandatory in any flow longer than one step.
- If the user backs out and re-enters, restore what they had. Drafts must persist across sessions for any flow > 60 seconds of input.
- Closing a modal should never be the only way to commit changes. "Done" or "Save" must be explicit.

The cost of a destroyed draft is not the minutes lost — it is the user learning to mistrust your product.

## 6. Surface the next step in context

After completing a step, the next step should appear *in the current context*, not require the user to navigate back to a hub.

- After uploading a file, offer "Share" or "Open" inline. Do not return to the file list.
- After creating an item, offer "Add another" *and* "View" inline. Force neither.
- After completing a multi-step form, the success screen should anchor the next likely action ("View your account" or "Send your first invoice"), not just say "Done."

This is the principle behind "wizards that do not feel like wizards" — the user never leaves the work to manage the work.

## 7. Pages vs panels vs modals

Different containers signal different commitments to the user.

| Container | Use for | Cost |
|---|---|---|
| Page | A new task, persistent context | Full transition, browser history |
| Panel/drawer | Detail of the current task, related context | Visible parallel state |
| Modal | A decision that blocks the current task | Interrupts attention, must be dismissed |
| Inline expand | A detail of one row/item | No context loss |

- Default to inline expand, then panel, then page. Modal is last.
- Never put a multi-step flow in a modal. If it needs steps, it needs a page.
- A panel that obscures critical context (the thing the user was reading) is a modal in disguise.

## 8. Dashboards: rank by decision, not by volume

A dashboard exists to support decisions, not to display everything.

- Rank widgets by the urgency and frequency of the decisions they support. The most acted-upon metric goes top-left.
- "Total users" is rarely a decision. "Users blocked from completing signup" is.
- Default time range matches the cadence the user actually operates on (daily ops? show today. weekly review? show 7 days). Time range is a default, not just a control.
- Empty widgets must say what they would show, not just "No data."

## 9. Search vs browse vs filter

These three are not interchangeable.

- **Browse**: the user does not know exactly what they want; they recognize it when they see it. Provide structure and categories.
- **Filter**: the user knows the rough shape; they want to narrow a known set. Provide combinable, non-destructive controls.
- **Search**: the user knows what they want and can name it. Provide a single field with fast, forgiving matching.

Most products need all three. Picking only one forces users into the wrong tool for their situation.

## 10. Onboarding is the first flow, not a separate one

Onboarding is not a setup wizard before the real product. It is the first lap through the same product, with extra scaffolding.

- Ask only what is needed to complete the *next step*, not the whole profile.
- Defer everything optional. Settings can be configured later; the empty profile can be filled later.
- The first session should produce a real, persistent artifact the user can return to. A real document, a real project, a real list — not a "demo" that gets thrown away.
- Skip is a first-class option at every step. A user who skips and succeeds is a better outcome than a user who completes and abandons.

## 11. Empty states are entry points

The first time a user sees a screen, it is empty. That empty state is the most important version of the screen.

- Explain what this screen will hold once it has content.
- Offer the single most likely first action.
- Show an example or template if the action is non-trivial.
- Never just say "No items." That is a missed conversation.

## 12. Navigation should reveal where you are, where you can go, and where you've been

- "Where you are" — the active state in primary navigation, the page title, the URL.
- "Where you can go" — visible primary nav at all times, predictable secondary nav per section.
- "Where you've been" — visited link styling matters more than designers think. Persistent recently-viewed lists for content-heavy apps.

A user who is lost will leave. A user who is oriented will explore.

## 13. Anti-patterns

- **Hamburger menu hiding primary nav on desktop.** Discoverability collapses; primary actions get used less.
- **Bottom tab bars on screens that need to scroll past 5+ items per tab.** Users lose track of which tab they are in.
- **Hub-and-spoke where every action returns to the hub.** Forces the user to re-orient after every action.
- **Modal-on-modal.** If a modal needs another modal, the first should have been a page.
- **"Are you sure you want to leave?" prompts for routine navigation.** Train users to dismiss them and lose real warnings.
- **Search that requires exact spelling.** Use forgiving matching by default; surface "Did you mean" only as a secondary suggestion.
- **Policy maze explained with UI chrome.** If a path is complex because the rule is complex, do not hide that behind steppers, tooltips, or clever navigation. Simplify the rule or expose the trade-off.

## 14. Quick checklist

When reviewing a flow or IA, ask:

- [ ] Can I describe each screen's primary decision in one sentence?
- [ ] Can I describe each screen's core message in one sentence?
- [ ] Is any confusing branch caused by a policy or eligibility rule that can be simplified?
- [ ] Is there exactly one primary action per screen?
- [ ] Are groupings based on user tasks, not on the data model?
- [ ] Is navigation depth ≤ 2 (3 with strong reason)?
- [ ] Does every flow have a clear exit that preserves work?
- [ ] After each step, is the next step visible without going "home"?
- [ ] Are empty, loading, and partial states designed, not afterthoughts?
- [ ] Does onboarding ask only what the next step needs?
