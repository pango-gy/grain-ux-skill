# Trust, Consent & Agency

Open this file when designing or reviewing: sharing, publishing, billing, privacy, permissions, notifications, AI-generated output, automation, destructive actions, data export/import, account settings, or any flow where the system can surprise the user.

## Contents

- Do not surprise the user
- Consent must be specific
- Preview before external impact
- Automation serves agency
- AI output needs inspection
- Permissions should explain consequences
- Billing and plans must be legible
- Respect beats conversion pressure
- Auditability is part of UX
- Anti-patterns
- Quick checklist

## 1. Do not surprise the user

Surprise is a trust failure. Users should never wonder, "Wait, did it just send, charge, delete, share, or publish that?"

Before any high-stakes action, the interface must make three things visible:

- What will happen.
- Who or what will be affected.
- Whether and how it can be undone.
- Why the action is worth taking now, if the user must spend money, trust, private data, or time.

If the consequence cannot be summarized clearly, the action is not ready to be one click.

## 2. Consent must be specific

Consent is not a checkbox-shaped formality. It is the user's informed agreement to a specific consequence.

- Ask for consent at the moment it matters, not only during onboarding.
- Name the object, audience, destination, and duration where relevant.
- Separate required consent from optional marketing or tracking consent.
- Do not bundle unrelated agreements into one control.
- Let users revoke consent where revocation is meaningful.

The more permanent or external the consequence, the more explicit the consent must be.

## 3. Preview before external impact

Anything that leaves the user's private workspace deserves a preview.

- Sending messages, invites, invoices, and emails.
- Publishing pages, posts, listings, or reports.
- Sharing files, dashboards, records, or links.
- Running imports, syncs, or bulk edits.
- Triggering automations that act on behalf of the user.

The preview should show the real audience, real content, real timing, and real permissions. A generic "Are you sure?" does not create trust.

## 4. Automation serves agency

Automation should reduce repetitive work, not remove control. Users need to understand what the system did, what it will do next, and how to intervene.

- Show pending, running, completed, failed, skipped, and cancelled states.
- Explain why an automation acted when the reason is not obvious.
- Allow pause, cancel, undo, or edit-before-run where stakes justify it.
- Surface logs or history for actions that affect other people or durable data.
- Do not silently change future behavior based on hidden inference.

Automation is trustworthy when the user can predict it and stop it.

## 5. AI output needs inspection

Generated output is not user intent until the user accepts it. Treat AI as a drafting surface, not an invisible actor.

- Preview generated text, images, code, emails, reports, and edits before sending or publishing.
- Mark uncertainty, assumptions, sources, and missing context when they matter.
- Make regenerate, edit, accept, and discard distinct actions.
- Keep original user input recoverable.
- Require explicit approval before irreversible, external, financial, legal, or account-level action.

The user owns the outcome. The interface must give them enough control to own it honestly.

## 6. Permissions should explain consequences

Permission prompts are trust moments. Users need to know why access is requested and what changes after granting it.

- Ask for the smallest permission that completes the current task.
- Request permission in context, not before the user sees value.
- Explain what the permission enables in user terms.
- Show who has access to shared objects.
- Make permission changes auditable for teams and high-stakes data.

"Allow access" is not enough when the user cannot see what access means.

## 7. Billing and plans must be legible

Money raises stakes. Pricing UX should reduce ambiguity, not optimize confusion.

- Show price, billing interval, renewal date, tax/fees, and cancellation effects before purchase.
- Do not hide limits that can create surprise cost.
- Warn before a trial converts, a quota is exceeded, or a paid action runs.
- Make downgrade, cancellation, and data retention consequences explicit.
- Avoid "unlimited" when cost, performance, or fair-use limits exist.

Trust lost in billing is rarely recovered by better UI elsewhere.

Respect beats conversion pressure. Do not trade long-term trust for a short-term click by hiding effort, risk, limitations, or cost until after commitment. Friendly copy cannot make a concealed trade-off respectful.

## 8. Auditability is part of UX

When actions have durable or shared consequences, users need a way to reconstruct what happened.

- Show who changed what and when.
- Distinguish user actions from system or automation actions.
- Keep status history for background jobs.
- Provide receipts for sends, publishes, payments, imports, and permission changes.
- Make recovery paths visible from the history when possible.

An audit trail is not only for compliance. It helps users feel oriented after time passes.

## 9. Anti-patterns

- **Bundled consent.** One checkbox accepts unrelated consequences.
- **Publish/send without preview.** External impact happens before inspection.
- **Silent automation.** The system acts and leaves no visible reason or history.
- **AI auto-commit.** Generated output affects others or durable data without approval.
- **Hidden paid limit.** The user learns the cost only after crossing it.
- **Permission prompt on first load.** The product asks for trust before earning context.
- **Dark default.** The default benefits the business while surprising the user.
- **Benefit exaggerated, cost deferred.** The user sees the upside before commitment, but limits, effort, cancellation, data use, or downside appear only afterward.

## 10. Quick checklist

When reviewing trust, consent, and agency:

- [ ] Will the user be surprised by who, what, when, where, or cost?
- [ ] Is consent specific, timely, separable, and revocable where possible?
- [ ] Is there a real preview before send, publish, share, import, or automation?
- [ ] Can the user pause, cancel, undo, or edit automation when stakes justify it?
- [ ] Does AI output require explicit acceptance before durable or external action?
- [ ] Are permissions and billing consequences explained in user terms?
- [ ] Are cost, effort, risk, and limits visible before conversion pressure?
- [ ] Can the user later see what happened and who or what caused it?
