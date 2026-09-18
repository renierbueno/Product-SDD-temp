---
name: lock-content-voice
description: Use when it's time to lock (or deliberately revisit) the product's voice, tone, and real copy — the equivalent of establish-design-system but for words, not color. Without this, content gets decided on the fly inside build-prototype, the same drift that already happened with palette and typography before establish-design-system existed. Produces a locked voice doc (actionable principles with Do/Don't examples, not loose adjectives) plus the real, closed copy for the site's key pieces, not an open list of drafts.
---

# Lock the voice and content

Goal: decide ONE time how the product sounds — and write the real copy for the pieces blocking the build — not re-decide it every time a prototype gets built.

## When to use it

- There's real content pending (a vague headline, a section that "doesn't sound like me," text that isn't in its final version yet) and it's blocking marking something FINAL in `finalize-product-design`.
- Someone says something "doesn't sound human" or "this is it, not me" — that's the signal the conversation left structure/flow and entered voice. Stop it and move it here, don't seed it inside `build-prototype`.
- The product has a real voice already demonstrated somewhere else (a real writing sample, an existing voice guide) that needs inheriting, not inventing from scratch.

## What this skill is NOT

- **Doesn't decide visual identity.** That's `establish-design-system`. This skill decides words, not colors.
- **Doesn't decide structure or flow.** That already happened in `build-prototype`/`prioritize-roadmap`. This skill assumes the structure is already decided and writes the copy that goes inside it.
- **Doesn't invent facts.** Any data, figure, or claim comes from the same sources of truth the rest of the harness already uses (`doc_company_context.md`, the project's content-bank) — this skill decides HOW it's said, never WHAT gets claimed.
- **Isn't an adjective exercise.** "Warm, direct, approachable" isn't a voice guide — it's a wish list. The output has to be actionable: real Do/Don't examples, not loose attributes (verified 2026-09-17, real content-design practice: a voice guide with no concrete examples doesn't change how anyone writes).

## Inputs (read these before proposing anything)

- Any REAL existing writing sample from the subject (a voice guide, a real email, a real answer to a question) — the voice gets inherited from there, not invented. If there's none, say so explicitly before proposing anything.
- `docs/doc_company_context.md` — who the audience is, what they already know, what register is needed (check discovery for a note on this if one exists).
- Real feedback already given on existing content (what got rejected and why) — this is the strongest signal of all, stronger than any template.

## Process

**Step 1 — Extract the voice from real samples, don't invent it.** Read the existing voice material line by line. Identify concrete, repeatable patterns: which words it avoids, how it opens a sentence, how it closes one, how formal it is, where it uses dry humor vs. where it doesn't. Every pattern has to point to a real sample, not to a gut feeling about "how it should sound."

**Step 2 — Turn each pattern into a Do/Don't rule with an example.** "Direct" isn't a rule. "Doesn't open with a rhetorical question; states the fact first" with a real example next to it, is. At least 5 rules, each with a Do example and a Don't example pulled from real feedback already given (verified 2026-09-17, STRONG signal: a voice guide with no concrete example per rule doesn't get others to write differently).

**Step 3 — Map tone by context, not one single tone for everything.** The same product sounds different in a headline than in an error message (verified 2026-09-17, standard content-design practice: voice stays constant, tone varies by scenario). List the product's real contexts (headline, case study, error message, CTA, meta description) and what changes in each one.

**Step 4 — Write the real copy for the blocked pieces, closed.** Not "here are three versions of the headline" indefinitely — one final decision per piece, with discarded alternatives briefly noted (what was tried, why not). Every piece of copy has to trace back to a real fact (`doc_company_context.md`/content-bank) if it claims something, never invented.

## Expected output

```
Voice rules (Do/Don't, with an example each): [minimum 5]
Tone by context: [headline / case study / error / CTA / meta — what changes in each]
Locked copy — blocked pieces: [every real headline/section, final version, traceable to a fact if it claims something]
What got discarded and why: [brief, per piece]
Status: [LOCKED — dated — or ON HOLD / EXPLORED NOT CLOSED, never ambiguous]
```

Save the complete result to `docs/doc_voice.md`. If the status is ON HOLD, say so explicitly.

## How it connects with the rest

Receives from `discovery-operator` (register/name already decided) and from any real voice sample already existing outside the harness. A later `build-prototype`/`finalize-product-design` reads `docs/doc_voice.md` instead of writing new copy every time. `finalize-product-design` can't mark a screen FINAL if its copy doesn't come from here.

## Not complete if...

- Not complete if the voice rules are loose adjectives with no Do/Don't example.
- Not complete if any voice pattern can't be traced to a real writing sample from the subject.
- Not complete if tone was treated as a single one for the whole product, with no variation by context.
- Not complete if the copy for a blocked piece claims something that isn't in `doc_company_context.md` or the content-bank.
- Not complete if it's left as several open versions with no final decision per piece.
- Not complete if the result wasn't saved to `docs/doc_voice.md`.
