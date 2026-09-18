---
name: build-prototype
description: Use to generate a functional prototype (single-file HTML/React) that shows a flow instead of describing it. Used to validate UX and scope before committing engineering, and to show something tangible instead of describing it in a meeting. Reads the applicable context docs before inventing anything, identifies the peak moment and the close before building, and gets checked against a real usability and accessibility floor, not just "it works."
---

# Build a prototype with AI

Goal: show the flow, don't tell it. A prototype that doesn't really work but reveals the UX and scope decisions you made, built by you in minutes — and that feels like the real product, not a generic mockup.

## When to use it

- You're asked for a product feature and want to show what it would look like.
- You need to validate a flow with a user without waiting for engineering.
- You want to align Commercial or Leadership on scope before committing engineering.

**This validates ONE flow, it's not the final design of the whole product.** A prototype — even a high-fidelity one — is a fast, disposable validation tool, not the complete and definitive inventory of every real screen/state (verified 2026-09-17, MEDIUM-STRONG signal: even within the same design role, "high-fidelity mockup" and "prototype" are listed as distinct deliverables). Once the flow is validated and it's time to produce the complete design of every real screen for handoff to engineering, that's `finalize-product-design` (`/finalize-design`), not more one-off prototypes.

**Fidelity, LOW by default.** Unless explicitly asked, this prototype is low fidelity: gray/neutral palette and typography, but with real content and real voice (see Inputs below) — "low fidelity" never means generic content, it only means no visual identity. Don't wait for a design system to exist — the standard industry order is the reverse (research → low-fidelity flow → high-fidelity visual design, verified 2026-09-17, NN/g and UX process guides, STRONG signal). Only move to HIGH fidelity if explicitly asked, and in that case read `docs/doc_design_system.md` first — if it doesn't exist, say so and suggest `establish-design-system` (`/design-system`) before inventing a palette.

Don't use this to decide or iterate on the visual identity itself (palette, typography, look-and-feel) at ANY fidelity — that's always `establish-design-system` (`/design-system`). If the conversation starts circling around whether something "feels differentiated" or testing palettes, stop and move it there. The visual distinction (always neutral at low fidelity) is the only thing fidelity affects — content, voice, and structural mechanisms that are already validated do NOT degrade just because it's low fidelity.

## Inputs (read this before inventing anything)

Before building, read the context docs that apply — each one feeds something different, and each one prevents a type of invention:

- **`docs/doc_company_context.md`** — who the real user/operator is, what real facts already exist (content, figures, cases). Use it instead of inventing who the audience is or what the product says.
- **`docs/doc_market_research.md`** — how this audience actually behaves in this type of context (reading speed, arrival channel, expected attention). Use it to decide how fast the prototype has to "land," don't assume it.
- **`docs/doc_open_questions.md`** — what's NOT confirmed yet. If the prototype needs an answer that lives here, don't invent it: state it explicitly in the prototype or in your response ("this assumes X, unconfirmed — see doc_open_questions.md").
- **`docs/doc_design_system.md`** — locked visual identity, only if the prototype is high fidelity (see above).
- **`docs/doc_voice.md`** — locked voice and copy, if it exists. Use it as-is for any headline/copy that's already locked there; don't rewrite it. If the copy you need isn't locked yet, say so and suggest `lock-content-voice` (`/voice`) instead of writing new copy on the fly — same treatment as the design system for color.

**Content rule: real first, invented only if missing.** Any data, figure, or text that already exists in these docs (or in the project's content-bank/source of truth) gets used as-is — never generic, never a placeholder. Only invent what's genuinely not covered, and in that case mark it as such (same [CONFIRMED]/[ASSUMPTION] criteria as the rest of the harness), never present it as if it were a real fact. This isn't just data hygiene — real content (no lorem ipsum, no generic filler copy) is what makes a prototype give useful feedback instead of an empty reaction to filler text.

## The peak moment and the close (before building)

Before drawing anything, identify two concrete moments in the flow — don't treat them as a flat list of equally important screens:

- **The peak**: the moment in the flow that will weigh most in how someone remembers and judges the whole experience (the strongest proof, the most surprising result, the step where the real value becomes obvious).
- **The close**: the last screen or action before the person decides to continue or leave.

Design them with more care than the rest — the Peak-End Rule (Yablonski, *Laws of UX*) says people judge an experience by its peak and its ending, not by the average of every step. A prototype that treats its five screens as equally important is leaving this on the table. Say it explicitly in your response: "this flow's peak is X, the close is Y" — don't leave it implicit.

## How to ask the copilot for it

Give it context in this order:

```
Build an artifact [single-file HTML / React] that shows:
- Screen: [e.g. the payment terminal asking for an email after a purchase]
- The peak and the close of this flow: [which ones, before building]
- States to show: [happy, error, edge]
- Data: [real, from the context docs first; anything invented, marked as such]
- Constraint: no backend, everything in local state, no browser storage libraries
- Brand: neutral colors by default (low fidelity). If high fidelity, read `docs/doc_design_system.md` and use it as-is, don't reinvent it; if that doc doesn't exist yet, say so and suggest `/design-system` instead of improvising one.
```

## What to show, by problem type

- **Post-transaction capture**: a screen after completing an action with a contact field + a value hook (cashback, warranty, content). Shows the trade-off: friction vs. capture.
- **Campaign/operations dashboard**: a backoffice view where someone creates or manages something (format, goal, budget, report). Shows the full lifecycle.
- **New-vertical feature**: the key screen in that vertical's user flow.

## The UX laws that always apply (Yablonski, *Laws of UX*)

Not a list to cite, it's meant to be applied in every layout/content decision:

- **Jakob's Law**: people expect something new to work like what they already know. Navigation, forms, basic patterns → conventional. Spend the "different" budget only on what's genuinely the differentiator, not on reinventing a menu.
- **Hick's Law**: more options = slower decisions. Fewer nav items, one clear CTA, not several competing.
- **Peak-End Rule**: see the section above — identified BEFORE building, not after.
- **Aesthetic-usability effect**: an interface that looks better is perceived as more usable, and the first impression forms in milliseconds and rarely changes afterward (see `doc_market_research.md` if the project has a real figure on this for its audience). This is the functional reason, not just an aesthetic one, high fidelity matters when it's time to use it — it's not visual vanity.

## Usability checklist (Nielsen, before calling it done)

Check it against the prototype, not just against the happy path:

1. Visibility of system status — is it clear what's happening at each moment?
2. Match with the real world — is the language and are the concepts the ones the audience already uses?
3. User control and freedom — is there a clear way out of any unwanted action?
4. Consistency and standards — does the same action behave the same way throughout the prototype?
5. Error prevention — can the error be avoided before it happens, not just shown after?
6. Recognition over recall — is the needed information visible, or does it have to be memorized?
7. Flexibility and efficiency — does it work equally well for a first-time viewer and a returning one?
8. Aesthetic and minimalist design — is there anything on screen that doesn't serve the main goal?
9. Help recognizing, diagnosing, and recovering from errors — does the error message say what happened and what to do, in plain language?
10. Help and documentation — if something needs explaining, is it where it's needed, not hidden away?

## Accessibility floor (non-negotiable, at any fidelity)

- Real semantic HTML (`<button>`, `<a>`, `<label>` with its `for`) instead of `<div>`/`<span>` styled as a button — the browser's native accessibility doesn't need to be rebuilt by hand when it doesn't have to be.
- Minimum text contrast 4.5:1 (3:1 for large text) — holds even at low fidelity in gray.
- Everything works by keyboard: Tab/Shift+Tab navigates, Enter/Space activates, Escape closes overlays. Never a trapped focus.
- Visible focus state always (minimum 3:1 contrast between focus and non-focus) — never `outline: none` without a real replacement.

## Rules

- A single file, no heavy external dependencies.
- No localStorage/sessionStorage (doesn't work in artifacts): use in-memory state.
- Real content first (see Inputs); anything invented, marked as such — never lorem ipsum, never generic filler copy.
- Show the error and edge states, not just the happy path. That's where the real scope problems hide.

## Why prototype before asking engineering

Prototyping this before asking engineering rules out obvious UX or scope problems. That way the PM isn't the bottleneck, and engineering receives something already validated.

## Expected output

An artifact that opens and lets you navigate the flow, with the peak and the close named explicitly in your response, not just built into it.

## How it connects with the rest

Used alongside `write-spec`, doesn't replace it: the spec (in its first pass, the draft) originates the prototype; the prototype is the UX and scope validation before handing off to engineering. Reordered 2026-09-17: runs right after the spec draft, BEFORE `validate-fast`/`human-validation` and before `establish-design-system`/`lock-content-voice` — the low-fidelity prototype is the cheap validation that decides whether it's worth investing in the next ones. At low fidelity it doesn't depend on `establish-design-system` at all. At high fidelity (once the flow is already validated), it reads `establish-design-system`'s result (`docs/doc_design_system.md`) — if that skill hasn't run yet, that's the one to invoke first, not a variant of this one. Once the flow is validated and, if applicable, identity/voice are locked, `finalize-product-design` is the next step for the complete inventory — don't keep running more high-fidelity prototypes as a substitute for that.

## Not complete if...

- Not complete if only the happy path is shown, with no error or edge state.
- Not complete if it doesn't come with the spec that originated it.
- Not complete if it uses localStorage/sessionStorage or depends on a real backend.
- Not complete if it had to iterate on palette/typography/visual identity more than once inside this skill, at any fidelity — that's the signal the conversation moved into `establish-design-system` work and should continue there, not here.
- Not complete if it didn't read the applicable context docs before inventing data, or if it presented invented content as if it were a real fact without marking it.
- Not complete if it didn't explicitly name the flow's peak moment and close before building.
- Not complete if it violates any of the 10 points of the Nielsen checklist or the accessibility floor — both are part of "done," not an optional extra.
