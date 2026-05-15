# Forms & Input

Open this file when designing or reviewing: forms, settings, search fields, filters, multi-step input, onboarding questions, validation, uploads, import flows, or any UI where the user must provide, choose, edit, or confirm information.

## Contents

- Input is work
- Show value before asking
- Order fields by user reasoning
- Required and optional must be obvious
- Validation timing follows intent
- Inputs should match the data
- Multi-step forms need memory and progress
- Search and filters are input too
- File and import flows need previews
- Anti-patterns
- Quick checklist

## 1. Input is work

Every field asks the user to spend attention, memory, trust, and sometimes private information. Treat each field as a cost that must earn its place.

- Show the value before the cost. If a field is sensitive, private, high-effort, or surprising, the user should already know what they get for answering.
- Ask only what is needed for the next decision or outcome.
- Explain why sensitive or surprising information is needed.
- Prefer choosing from known options over typing from memory.
- Preserve entered data across errors, navigation, refresh, and network failure.
- Never make users repeat information the system already knows.
- If the user cannot answer quickly, split the question, offer examples, recommend a default, or use information the system already has.

If a field does not change what the product can do next, remove it or defer it.

## 2. Order fields by user reasoning

Field order should match how the user thinks about the task, not how the backend stores data.

- Start with the anchor: what is being created, sent, changed, or searched.
- Group fields that answer the same decision.
- Put dependent fields after the field that controls them.
- Keep advanced, rare, or administrative fields behind progressive disclosure.
- Put destructive or high-stakes confirmation at the end, after consequences are visible.

A form should feel like a conversation with a competent person, not a database migration.

## 3. Required and optional must be obvious

Users should know the rules before they break them.

- Mark required fields before input, not after submit.
- Prefer marking optional fields when most fields are required.
- Avoid hidden requirements inside placeholder text.
- Explain format rules near the field when the format is not obvious.
- Do not disable submit without explaining what is missing.

The best required-field UX prevents an invalid submit without making the user hunt.

## 4. Validation timing follows intent

Validation should help the user finish, not punish them for starting.

- Validate on blur for most fields.
- Validate as typed only for hard limits, password strength, masks, and live previews.
- Validate on submit as a final pass, then focus the first invalid field.
- Validate server-only rules after submit or after a deliberate availability check.
- Do not show "Required" on first focus.

Validation copy should say how to fix the value, not only that it is wrong.

## 5. Inputs should match the data

The control should make invalid input hard and valid input easy.

- Use email, phone, URL, number, date, search, and password input types when appropriate.
- Use select, radio, segmented control, checkbox, slider, stepper, or autocomplete when the valid set is bounded.
- Avoid free text when spelling, casing, or exact terms matter.
- Use masks only when they reduce ambiguity; do not fight paste or autofill.
- Support paste, drag-and-drop, autocomplete, password managers, and browser autofill.

Do not make users adapt to implementation details the UI could encode.

## 6. Multi-step forms need memory and progress

Break long forms when fields are independent or conditional. Keep one screen when fields must be compared together.

- Each step should have one primary decision.
- Show progress in human terms, not only a step count.
- Back must preserve data.
- Save draft state automatically for flows longer than 60 seconds.
- Review screens should show what will happen, not merely echo inputs.

Users should always know how much work remains and whether leaving will cost them.

## 7. Search and filters are input too

Search and filter input changes what the user believes exists. Make that state visible.

- Show active filters near the results.
- Offer one action to clear filters.
- Preserve filters when drilling into a result and returning.
- Distinguish no results from no data.
- Use forgiving matching for search; exact-match search should be an explicit advanced behavior.

A filtered empty state should never look like the product is empty.

## 8. File and import flows need previews

Uploads and imports are high-uncertainty input. The user needs confirmation before the system mutates data.

- Show file name, size, type, and upload progress.
- Validate early and list row-level errors where possible.
- Preview parsed data before import.
- Let users download or copy an error report.
- Keep partial success visible and retry failed rows without re-uploading everything.

Never make a user discover import failure only after the original file context is gone.

## 9. Anti-patterns

- **Placeholder-only labels.** The prompt vanishes once typing starts.
- **Disabled submit with no reason.** Users cannot tell what to fix.
- **Validation while typing normal text.** The form scolds before the user finishes.
- **Resetting fields after an error.** The product destroys the user's work.
- **Optional fields asked up front.** The product taxes the majority for edge-case data.
- **Format rules after failure only.** The user could not have known the rule.
- **Import without preview.** Bulk changes happen before the user can inspect them.
- **Sensitive question before value.** The form asks for phone, identity, payment, permission, or private data before the user understands why it matters.
- **Recall test disguised as input.** The user must remember an ID, exact name, date, or setting the system could search, suggest, or retrieve.

## 10. Quick checklist

When reviewing forms and input:

- [ ] Does every field earn its cost right now?
- [ ] Is value visible before sensitive, private, or high-effort input?
- [ ] Are hard questions split, suggested, prefilled, or retrieved where possible?
- [ ] Are fields ordered by the user's reasoning, not backend shape?
- [ ] Are required, optional, and format rules visible before failure?
- [ ] Does validation happen at the right time and focus the first error?
- [ ] Does the control type prevent avoidable invalid input?
- [ ] Is input preserved across errors, back navigation, refresh, and network failure?
- [ ] Do search, filters, upload, and import flows make their current state visible?
