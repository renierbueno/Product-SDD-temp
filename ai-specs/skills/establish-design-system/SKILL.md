---
name: establish-design-system
description: Use when it's time to lock (or deliberately revisit) the product's visual identity — a palette with a real scale and semantic tokens, typography with a real scale, systematic spacing, elevation if applicable, validated contrast, a distinctive layout motif — for a HIGH-fidelity version. Not a prerequisite for a low-fidelity prototype (that's still build-prototype in gray/neutral), nor a monetization-model decision (that's design-monetization-model). Produces a locked, documented design system, accessible by construction, with real craft (not a flat 5-color palette) that the rest of the harness reuses.
---

# Lock the design system

Goal: decide the product's visual identity ONE time, not re-decide it on every high-fidelity prototype.

## When to use it

- The project needs a HIGH-fidelity version (with real branding, not gray/neutral) of something for the first time — not just validating a flow.
- Someone asks to explore "design directions," palettes, typography, or says something "doesn't feel differentiated/unique" — that's the signal the conversation left flow validation and entered identity. Stop it and move it here, don't keep resolving it inside `build-prototype`.
- It gets deliberately revisited when the brand context genuinely changed (e.g. a brand decision already locked on another channel, like a LinkedIn banner, that now has to stay consistent here), or when the project has grown enough that it's worth repeating Step 2's distinctiveness check (see below — it's a repeatable check, not a one-time filter).

## What this skill is NOT

- **Not a prerequisite for every prototype.** A low-fidelity prototype (gray/neutral, validates flow, scope, and error/edge states) doesn't need to wait on this — that's exactly what `build-prototype` already does by default. The standard industry order is research → low-fidelity flow → *then* visual/high-fidelity design, not the reverse (verified via research 2026-09-17: Nielsen Norman Group and multiple UX process guides agree visual fidelity gets applied at the high-fidelity stage, not before — STRONG signal, several independent sources converge).
- Doesn't validate a flow or error/edge states — that's still `build-prototype`, at any fidelity.
- Not a business-model decision — `design-monetization-model` decides HOW a touchpoint gets monetized, not how it looks.
- Doesn't repeat every session like `live-research` — it's locked once, and revisions are deliberate, never the result of "let's try some things" inside another skill.
- Not a complete component system (atomic design, a UI library) — that's longer-term engineering/product-design scope. This skill locks identity (palette, typography, spacing, elevation, a layout motif), it doesn't build a library.

## Inputs (read these before proposing anything)

- `docs/doc_company_context.md` — who the operator is, who the product is for, what tone/voice already exists in other real materials (CV, voice guide, public profiles).
- Any brand decision ALREADY locked on another channel (a palette chosen for a banner, a logo, a sibling product). This skill doesn't invent from scratch if there's already a real brand signal somewhere else — it inherits and reasons from it, doesn't contradict it without saying why.

## Process

**Step 1 — Find the real signal, not the template.** Look in the inputs for a specific detail about the subject (their own voice, a personal value, a brand decision already made on another channel) that no generic proposal would have. A palette or typography chosen "because it looks good" doesn't pass this step; it has to be explained from the subject.

**Step 2 — Avoid the AI default (a repeatable check, not a one-time one).** Before proposing, consciously compare against the known clichés (warm cream + serif + terracotta accent; near-black + a single neon accent; Inter/Space Grotesk as the "safe" typeface; everything in rounded-corner cards). If the proposal falls into one, change it and note what you changed and why. This check repeats every time the system is revisited (not just the first time) — a system that was distinctive six months ago can become generic if the whole category adopted it in the meantime.

**Step 3 — Build the palette as a real scale, not loose colors.** Standard industry practice (verified 2026-09-17, *Refactoring UI*, STRONG signal): a real palette has 8-10 shades of gray and 5-10 variations per key color, not 5 flat tokens. First the **primitives** (raw hex values, family name + scale — e.g. `graphite-800`), then the **semantics** (each primitive mapped to a usage role — e.g. `color-bg-default -> graphite-800`). When lightening or darkening, rotate the hue (toward yellow/cyan/magenta when lightening, toward red/green/blue when darkening) instead of just mixing in white/black — that keeps the color from washing out. Near the extremes (very light or very dark), raise saturation instead of letting it drop, or it looks washed out.

**Step 4 — Define a real typographic scale, not "2-3 sizes that look good."** Hand-pick a complete scale (e.g. 12/14/16/18/20/24/30/36/48/64px), not `em` units that can drift out of alignment. Line length 45-75 characters. Line-height scales INVERSELY to size: loose for small text, tight for large headlines.

**Step 5 — Define a non-linear spacing scale.** Values like 4/8/12/16/24/32/48/64px (~25% jump between adjacent values), not arbitrary numbers. More space AROUND a group than INSIDE it — that's how you perceive what belongs together, without needing a border.

**Step 6 — Elevation system, only if the design uses depth (cards, modals, dropdowns).** 3-5 real steps (e.g. button < dropdown < modal), each with its own blur/offset — never the same shadow reused everywhere. If the layout doesn't use depth, mark it N/A explicitly, don't omit it silently.

**Step 7 — Validate contrast BEFORE locking, not afterward, per prototype.** For every text/background pair the system will actually use, calculate and document the real contrast ratio (minimum 4.5:1 normal text, 3:1 large text and focus). Verified 2026-09-17 (STRONG signal, standard industry practice): accessibility gets validated at the token layer, it's not left for each prototype to discover on its own.

**Step 8 — Lock it, don't accumulate options indefinitely.** Present 2-3 real directions (not ten variations of the same one), let the operator choose or mix, and CLOSE: the output is a locked system, not an open list of possibilities.

## Expected output

```
Palette — primitives: [complete scale per color family, not 5 loose tokens]
Palette — semantics: [each primitive mapped to a usage role]
Typographic scale: [the complete hand-picked scale, with line-height per size]
Spacing scale: [the complete non-linear scale]
Elevation/shadows: [3-5 real steps, or explicit N/A if the layout doesn't use depth]
Validated pairs (contrast): [every real text/background combination in the system, with its calculated ratio]
Typography — families: [2-3 with their role — display / body / utility — and why this combination]
Distinctive layout motif: [1-2 sentences — the concrete mechanism that keeps this from being a generic template]
Final touches considered: [e.g. accent borders, fewer borders overall, intentional empty states — optional, only what's genuinely going to be used]
Image/icon style: [optional — only if the project actually uses them]
Why it fits the subject: [the real signal from Step 1, explicit]
What we deliberately did NOT do: [the cliché avoided in Step 2]
Status: [LOCKED — dated — or ON HOLD / EXPLORED NOT CLOSED, never leave it ambiguous]
```

Save the complete result to `docs/doc_design_system.md`. If the status is ON HOLD, say so explicitly — never let the doc read as locked when it isn't.

## How it connects with the rest

Receives context from `doc_company_context.md` and from any brand decision already locked outside the harness. A later HIGH-fidelity `build-prototype` reads `docs/doc_design_system.md` instead of deciding color/typography again — and since contrast is already validated per pair, that prototype doesn't have to re-check color accessibility, only use the documented pairs. A LOW-fidelity `build-prototype` doesn't depend on this skill at all — it can run before, in parallel, or before this skill even exists.

## Not complete if...

- Not complete if the palette or typography doesn't have a reason tied to the real subject, only "it looks good."
- Not complete if it wasn't consciously compared against the known AI-generated-design clichés.
- Not complete if the palette tokens are just raw values with no semantic layer.
- Not complete if the palette is a flat list of 5 colors instead of a real scale per family.
- Not complete if there's no hand-picked typographic scale, or a non-linear spacing scale.
- Not complete if the design uses depth (cards, modals) and there's no real elevation system, or if N/A wasn't explicitly marked when it doesn't apply.
- Not complete if any text/background pair the system actually uses doesn't have its contrast ratio documented.
- Not complete if it's left as an open list of options with no closed decision (or without explicitly marking ON HOLD).
- Not complete if the result wasn't saved to `docs/doc_design_system.md`.
