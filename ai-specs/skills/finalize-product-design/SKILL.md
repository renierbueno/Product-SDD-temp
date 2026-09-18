---
name: finalize-product-design
description: Use when the critical flow is already validated (build-prototype), the visual identity is already locked (establish-design-system), and the voice/copy is already locked (lock-content-voice), and it's time to produce the complete and final design of EVERY real screen and state in the product — not a fast validation of one flow, but the exhaustive reference engineering will build. Doesn't require every screen to have had its own prototype (that's not standard practice), but every screen that didn't must justify which already-validated pattern it reuses, carry the real why, and pass a viability check before being marked FINAL.
---

# Finalize the product design

Goal: produce the complete, polished design of every real screen and every real state in the product — the definitive artifact, not another validation. Real research (2026-09-17, MEDIUM-STRONG signal): even within a single design role, "high-fidelity mockup" and "prototype" are listed as DISTINCT deliverables — a prototype is a validation tool (fast, disposable, covers one flow), a final mockup/design is the complete reference engineering builds from.

## When to use it

- The critical flow is already validated (`build-prototype`, low or high fidelity), the visual identity is already `LOCKED` in `docs/doc_design_system.md`, and the voice/copy is already `LOCKED` in `docs/doc_voice.md` (if the project ran that skill — not every project needs it).
- There's a real inventory of screens/states that need final design, not just the example flow that was already prototyped.
- This is about to move to `/plan` (engineering) and the definitive reference is needed, not "just the home page's prototype."

**You don't need to prototype every screen one by one — that's not standard practice (verified 2026-09-17, STRONG signal: the real recommendation is to prototype only the critical/risky flows, 5-15 screens depending on complexity, not the complete inventory).** The rest's consistency comes from reusing the same components and patterns already validated, never from inventing something new without going through `build-prototype` first. That's why Step 2 below requires naming the reused pattern for every screen that didn't have its own prototype — if a real one can't be named, that screen needs to go through `build-prototype` before entering here.

## What this skill is NOT

- **Doesn't replace `build-prototype`.** Flow validation still happens there first, fast and disposable, for the critical flows. This skill assumes that validation already happened wherever it was needed.
- **Doesn't decide visual identity.** Applies `docs/doc_design_system.md` exhaustively; doesn't invent a new palette, typography, or layout motif. If an identity decision is needed that the locked system doesn't cover, that's the signal to go back to `establish-design-system`, not to decide it here.
- **Isn't more iteration on "how it looks."** By the time this skill runs, that question is already closed. This is about COVERAGE (every screen, every real state), not more direction.
- **Doesn't invent content.** The copy has to be in its final version (voice, positioning, wording), locked in `docs/doc_voice.md`, before entering here — if it isn't, that's `lock-content-voice` (`/voice`), not a gap to fill on the fly inside this one.

## Process

**Step 1 — Explicit inventory, nothing implicit.** List every real screen and every real state in the product, not just "the home page." Example of the level of detail: not "listing page," but "Catalog: 4 detail pages (or a template + 4 content variants), state with image / text-only state." Anything not designed in this pass gets marked DEFERRED with the reason, never silently omitted.

**Step 2 — For every screen with no prototype of its own, name the pattern it reuses.** "Reuses the listing card already validated in `checkout-hifi-b`" is a real justification; "looks similar" isn't. If there's no real pattern to name, that screen isn't ready for this skill — send it back to `build-prototype` first.

**Step 3 — Apply the locked system, don't reinvent it.** Every screen reuses the same tokens/typography/motif from `docs/doc_design_system.md`, and the copy from `docs/doc_voice.md` exactly as locked there. Zero new identity or voice decisions.

**Step 4 — Cover every screen's real states, not just the happy path.** Same standard as `build-prototype` (happy + error + edge), but now for the complete inventory, not a single flow.

**Step 5 — Say why each screen exists, not just what it contains.** One sentence per screen: what real user problem it solves, traceable back to discovery/`doc_company_context.md` (verified 2026-09-17: real design-team practice — the design file carries the problem and the why, not just the visual, so the decision can be audited later without guessing).

**Step 6 — Viability check before locking FINAL.** Does this screen depend on something that doesn't exist yet (a real screenshot, an integration, a data point)? If so, it's DEFERRED with that explicit reason, never FINAL with a placeholder in disguise (verified 2026-09-17: real practice — handoff reviews technical viability, not just visual accuracy, before calling something done).

## Expected output

```
Screen/state inventory: [complete list, each one FINAL or DEFERRED + reason]
Reused pattern (if it had no prototype of its own): [which one, and from where — never "looks similar"]
System applied: [confirms it comes from docs/doc_design_system.md, no new decisions]
Copy applied: [confirms it comes from docs/doc_voice.md, no new copy]
States covered per screen: [happy / error / edge, for every FINAL one]
Why it exists (per screen): [the real problem it solves, traceable to discovery]
Viability: [what depends on something that doesn't exist yet, and why it stayed DEFERRED]
What's out of this pass: [explicit, with a reason — never silent]
```

Save the result (or the pointer to the real artifacts) wherever the project keeps its prototypes — same criterion as `build-prototype`.

## How it connects with the rest

Receives from `build-prototype` (critical flows already validated), `establish-design-system` (identity already locked, `docs/doc_design_system.md`), and `lock-content-voice` (copy already closed, `docs/doc_voice.md`). Follow with `write-spec`'s second pass (reordered 2026-09-17): the spec gets closed here, with what actually got finalized, before moving to `/plan` — not directly from this skill to `/plan`. `/plan` takes the already-closed spec as the durable artifact, and this skill's inventory as the real reference the `engineer` agent builds from, not the validation prototype. Once it's actually built, verifying that what got built matches this (Design QA) is a real, distinct check this harness doesn't have as its own skill yet — pending a decision on whether one's needed, not assumed or resolved here.

## Not complete if...

- Not complete if the screen/state inventory isn't explicit — anything implicit or "assumed understood" doesn't count.
- Not complete if something was left out without explicitly saying it's deferred and why.
- Not complete if a new visual-identity decision was made inside this skill — that's the signal to go back to `establish-design-system`.
- Not complete if new copy was written inside this skill instead of using `docs/doc_voice.md` as-is — that's the signal to go back to `lock-content-voice`.
- Not complete if any screen's content isn't in its final version.
- Not complete if any screen marked FINAL only covers the happy path.
- Not complete if a screen with no prototype of its own doesn't name a real pattern it reuses.
- Not complete if any screen doesn't say what real problem it solves.
- Not complete if something was marked FINAL without passing the viability check.
