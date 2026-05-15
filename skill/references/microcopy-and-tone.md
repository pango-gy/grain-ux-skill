# Microcopy & Tone

Open this file when designing or reviewing: button labels, form fields, error messages, empty-state copy, onboarding instructions, system notifications, marketing-in-product (banners, badges), legal microcopy, or any text the user reads to make a decision.

## Contents

- Copy is the highest-leverage surface
- Buttons describe results, not actions
- Cut every word that does not change meaning
- Match the user's vocabulary
- Sentence case for everything except proper nouns
- Tone scales with stakes
- The aloud test
- Empty-state copy
- Error message copy
- Confirmation copy
- Notification, banner, and toast copy
- Onboarding copy
- Korean / English considerations
- Forbidden words
- Numbers, dates, times
- Quick checklist

## 1. Copy is the highest-leverage surface

A one-word change in a button label can move conversion more than a redesign. Copy is the interface most users actually consume — they skim the rest.

Two consequences:

- **Treat copy as a designed object.** Iterate it. Test it. Read it aloud.
- **Never let copy be the last thing decided.** "Lorem ipsum" in the mockup is a sign that decisions about the screen are still pending; you cannot design what is unsaid.

## 2. Buttons describe results, not actions

The label on a button should describe what will happen, in the user's own terms.

- "Submit" → "Send invite"
- "OK" → "Delete account" or "Save changes"
- "Cancel" → "Keep editing" (in a save-or-discard prompt)
- "Yes" / "No" → name both outcomes ("Delete file" / "Keep file")

Generic verbs (Submit, OK, Continue) are acceptable only when the action is genuinely generic. "Continue" is fine in a multi-step flow where every step continues; it is wrong on a delete confirmation.

Two-button dialogs should never read as "OK / Cancel." Both buttons should name their outcome — the user should be able to make the decision without reading the dialog body.

## 3. Cut every word that does not change meaning

Microcopy is read fast, skimmed faster. Every word the eye passes over before the meaningful one is a tax.

- "Please click here to continue" → "Continue"
- "You can now access your dashboard" → "Open dashboard"
- "We have successfully created your account" → "Account created"
- "Are you sure you would like to delete this?" → "Delete this item?"

A useful test: rewrite the sentence with half the words. If the meaning survives, the original was bloated. If meaning is lost, restore the smallest necessary word.

## 4. Match the user's vocabulary

Use the words the user uses, not the words the team uses internally.

- If users say "post," do not call it a "submission."
- If users say "team," do not call it a "workspace" (or vice versa — pick one and commit).
- If users say "send," do not call it "dispatch."
- Internal jargon (entities, resources, records, units, items) almost never wins.

When in doubt, listen to support transcripts or user interviews. The right word is the one already in the user's mouth.

## 5. Sentence case for everything except proper nouns

- ✅ "Create new project"
- ❌ "Create New Project"
- ❌ "CREATE NEW PROJECT"

Title Case Makes Buttons Feel Like Headings. ALL CAPS feels loud and slows reading.

Exceptions: proper nouns (brand names, product names), single-word labels that are inherently capitalized (acronyms).

## 6. Tone scales with stakes

| Stakes | Examples | Tone |
|---|---|---|
| Routine | "Saved.", "Welcome back" | Brief, neutral, can have personality |
| Transactional | "Invoice sent", "Payment received" | Specific, neutral, no flourish |
| Reversible-but-real | "Deleted. [Undo]" | Direct, brief, action available |
| Irreversible / legal / billing | "Your subscription will end on March 5" | Formal, complete, no joke |
| Catastrophic | "Your account was suspended" | Formal, specific, human contact named |

Personality is fine at the low-stakes end. It becomes inappropriate as stakes rise. A joke in a delete confirmation reads as careless; a joke in a billing failure reads as cruel.

Respect is part of tone. Copy should not make a cost sound smaller than it is, make a risky action feel routine, or hide a trade-off behind warmth. If the business wants the user to act, the copy still owes the user the full consequence before the button.

## 7. The aloud test

Read every important piece of copy aloud, to yourself, in a normal voice. If it sounds:

- **Stilted** ("Kindly proceed to the next page") — rewrite as you would say it to a coworker.
- **Robotic** ("Action completed successfully") — rewrite as a person would describe what happened.
- **Marketing-y** ("Get ready to supercharge your workflow!") — strip the adjectives.
- **Condescending** ("Don't worry, we've got you covered") — say it neutrally.
- **Cute when it should be neutral** ("Oopsie! Something went wonky") — kill the cute.

If you would not read the sentence aloud to a stranger across a table, do not put it in your product.

## 8. Empty-state copy

Empty states are the first conversation. Use them.

Template:

> [What this screen does in one sentence.]
> [Optional: why it's empty, if non-obvious.]
> [One specific first action, as a button or link.]

Example:

> Your saved searches will appear here.
> [Save your first search.]

Or:

> No invoices to review.
> When customers pay or fail to pay, those invoices will show up here.

Avoid: "No data," "Nothing yet," "Coming soon," generic encouragement ("Let's get started!").

## 9. Error message copy

See `errors-and-recovery.md` for the full theory. Copy-specific notes:

- Lead with what happened, in human terms.
- Avoid error codes in the visible text. (Include them in a secondary line only if support needs them.)
- Never use "Oops," "Whoops," "Yikes," or similar. They infantilize.
- Never use exclamation marks in error messages. Stakes are already raised.
- Identify the specific thing that failed, when you can. "Could not save *Q4 Report*. Try again."

## 10. Confirmation copy

- Name the object: "Delete *Q4 Report (2026)*?" not "Delete this?"
- The destructive button names the outcome: "Delete report," not "OK."
- The safe button names its outcome: "Keep report," not "Cancel."
- The body explains consequences when they are non-obvious. "This will also remove the 12 comments on this report."

## 11. Notification, banner, and toast copy

Each has a different cost; copy scales accordingly.

- **Toast** (4–6 seconds, dismissible) — one short sentence. "Project archived. [Undo]"
- **Banner** (persistent until dismissed) — slightly longer; reserve for important state. "You are viewing a draft. [Publish]"
- **Notification** (cross-session) — full sentence with context. "Alex commented on *Q4 Report*: 'Looks great...'"
- **Push notification** (cross-app) — under 60 chars on the alert; full content in the app.

Every notification should be actionable, dismissible, or both. Notifications that do neither are noise.

## 12. Onboarding copy

- Welcome screens with no value are skipped. Make the first screen produce a result.
- Tooltips on a tour should be ≤ 2 sentences. The first sentence names the thing, the second says what it does.
- Allow "Skip tour" at every step. Show it as a quiet text link, not a hidden gesture.
- After onboarding, never show "Welcome!" again. Use "Welcome back" sparingly, only when relevant.

## 13. Korean / English considerations

When the product ships in both languages, copy decisions interact:

- In code, do not hardcode new user-facing strings when a locale/i18n structure exists. Add them through the existing locale files and check the layout with the longest supported language.
- **Korean is denser.** A 5-word English button often translates to 2–3 Korean words. Layout that fits English may have awkward padding in Korean.
- **Politeness level (존댓말 / 반말).** Default to 존댓말 ("해요" or "합니다" form) for product surfaces. "해요체" reads warm but professional; "합니다체" reads formal and slightly distant. Pick one and apply consistently.
- **English imperative ≠ Korean imperative.** "Click here" → "여기를 클릭하세요" (polite) or "여기 클릭" (terse). Mood and politeness must match across the product.
- **Loan words.** Some English words have become Korean ("로그인", "이메일", "비밀번호"). Use them where standard. Forcing a pure Korean translation can read as archaic.
- **Don't translate marketing tone literally.** "Supercharge your workflow!" translates badly. Localize for what a Korean copywriter would write to the same audience.

When in doubt, write the Korean copy first as if there is no English, then translate the English to match the meaning — not the other way around.

## 14. Forbidden words

Words that are almost always wrong in product copy:

- "Simply", "just", "easily" — minimizes the user's struggle. If it were simple they would have done it already.
- "Please" — soft-padding that reads as servile. Reserve for genuine requests, not commands ("Please save before continuing" → "Save to continue").
- "Sorry" in microcopy — overused; loses meaning. Reserve for actual errors caused by you.
- "Oops", "whoops", "yikes" — infantilizes.
- "Don't worry" — invites worry by mentioning it.
- "We" in legalese — be specific (the company name) for legal text; "we" only for product voice.
- "Click here" — link text should describe the destination.
- Vague verbs: "manage," "handle," "process," "leverage." Replace with the specific verb.
- Over-softening risk: "small fee," "quick check," "just verify," "only takes a second" when the cost, effort, or privacy impact is real.

## 15. Numbers, dates, times

- Use numerals for numbers in UI ("3 items," not "three items").
- Dates: relative for recent ("2 hours ago"), absolute for older ("Mar 12"). Full date on hover.
- Times: 24-hour format is unambiguous; 12-hour is friendlier. Match user locale.
- Currency: always show the unit; never strip "$" or "₩" assuming context.
- Pluralization: "1 item" / "2 items" / "0 items" — never "1 items," never "item(s)."

## 16. Quick checklist

When reviewing copy:

- [ ] Do button labels describe the result of the action?
- [ ] Did I read every important sentence aloud?
- [ ] Did I cut every word that does not change meaning?
- [ ] Does tone match stakes (no jokes in errors, no formality in success toasts)?
- [ ] Does copy expose real cost, effort, risk, and limits before asking for action?
- [ ] Sentence case throughout?
- [ ] Empty states explain what the screen will hold and offer a first action?
- [ ] Errors say what, why, and what now — without blaming the user?
- [ ] Numbers, dates, currencies formatted consistently?
- [ ] Forbidden words ("simply," "just," "oops," "click here") absent?
