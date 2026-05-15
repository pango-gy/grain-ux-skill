# grain — UX review skill for AI agents

> Work with the grain of how people actually think, read, decide, trust, and recover.

**Languages:** [English](README.md) | [한국어](README.ko.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md)

Maintained by [Pango Gy](https://pango-gy.com).

`grain` is a portable AI agent skill for reviewing and shaping user-facing product decisions. It is not a visual theme, component library, or design system. It is a UX judgment layer that pushes back when a flow, form, error, AI action, permission prompt, or button label works against real users.

Use it alongside frontend builders, design-system skills, UI kits, and product code review. Those tools help agents build the interface; `grain` helps them notice whether the interface respects user effort, attention, accessibility, trust, and recovery.

## The Name

`grain` means the natural direction or texture of a material, like wood grain. To work "with the grain" is to move with that natural structure instead of fighting it. This skill uses the name because good UX follows how people actually think, read, decide, trust, and recover.

## Install

```bash
npx skills add pango-gy/grain-ux-skill
```

By default, the `skills` CLI installs project skills into `./.agents/skills/grain`. That shared directory is the project-level location used by universal agents such as Codex and Gemini CLI. Agents with their own project skill directory, such as Claude Code, get a symlink or copy when that directory exists in the project.

To materialize copies for every supported agent directory:

```bash
npx skills add pango-gy/grain-ux-skill --agent '*' --skill '*' -y --copy
```

Re-run the add command to update.

To remove:

```bash
npx skills remove grain
```

This removes the installed skill directories. If your project uses `skills-lock.json`, review that file after removal because the CLI may keep source metadata there for restore/update workflows.

## What Triggers It

`grain` activates automatically on user-facing decisions:

- Writing, refactoring, or reviewing UI components, screens, forms, and flows
- Designing or critiquing empty, loading, failed, partial, offline, and permission states
- Drafting copy, labels, microcopy, error messages, onboarding, or notifications
- Reviewing accessibility, keyboard behavior, focus order, touch targets, motion, and responsive behavior
- Designing forms, imports, filters, settings, permissions, sharing, billing, AI output, or automation
- Reviewing screenshots, prototypes, dashboards, internal tools, admin surfaces, or SaaS workflows

It should stay quiet for backend-only logic, infrastructure, or work with no user-facing behavior.

## What It Covers

Seven domains, one voice:

- **User flow & information architecture** — paths before pages, tasks before tables.
- **Cognitive load & simplicity** — fewer decisions, not just fewer clicks.
- **Forms & input** — every field earns its cost, validation helps instead of scolds.
- **Accessibility & inclusive interaction** — keyboard, touch, focus, motion, contrast, and viewport are baseline UX.
- **Trust, consent & agency** — no surprising sends, shares, charges, deletes, AI commits, or automations.
- **Errors, edge cases & recovery** — empty/loading/failed/offline as first-class screens, undo over confirm.
- **Microcopy & tone** — buttons describe results, errors do not blame, every sentence passes the aloud test.

Each domain has a deeper reference under [`skill/references/`](skill/references). `SKILL.md` tells the agent when to load each reference so the main skill stays focused.

## Core Philosophy

`grain` applies these laws first:

- Make the next action obvious.
- Simplify the rule before the screen.
- Show value before asking for effort.
- Preserve user effort.
- Do not surprise the user.
- Let users undo, not just confirm.
- Treat accessibility as baseline UX, not a mode.
- Design failure states as part of the product.

The full set of laws, domain routing, and anti-patterns lives in [`skill/SKILL.md`](skill/SKILL.md).

## Positioning

`grain` is strongest as a companion skill:

- Pair it with a **frontend builder** to catch UX regressions before code lands.
- Pair it with a **design system** to make sure components are used for the right task, not only styled correctly.
- Pair it with an **AI/automation tool skill** to require previews, consent, status, history, and explicit approval before durable or external actions.
- Pair it with a **product review workflow** to turn vague feedback into concrete laws and anti-patterns.

It does not generate a visual identity, choose a brand palette, or replace product research. It gives agents a reusable UX standard for decisions they already make while coding or reviewing.

## Example Review Prompts

```text
Use grain to review this checkout flow for trust, consent, and recovery.
```

```text
Use grain while refactoring this settings form. Preserve input and improve validation UX.
```

```text
Use grain to check whether this AI-generated email flow needs preview, edit, and approval states.
```

```text
Use grain to review this dashboard for cognitive load, accessibility, and empty states.
```

## Author

Pango Gy CTO 유승재 ([pinkyooysj@pango-gy.com](mailto:pinkyooysj@pango-gy.com))

Company: [Pango Gy](https://pango-gy.com)

## License

[MIT](LICENSE). Use it, fork it, rewrite it in your own voice. The point is that more products treat UX as a first-class concern.

## Lineage

Stands on the shoulders of Donald Norman, Jakob Nielsen, Steve Krug, Bruce Tognazzini, Alan Cooper, Dan Saffer, and Edward Tufte. See the `Lineage` section in [`skill/SKILL.md`](skill/SKILL.md) for which idea came from where.
