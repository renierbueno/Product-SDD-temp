# product-sdd — Spec-Driven Development Harness

Portable scaffolding for taking a product idea from zero to validated without being engineering's bottleneck. It's meant to be used with Claude, Cursor, or Codex interchangeably: there's a single canonical source in `ai-specs/` and each copilot reads from there.

The philosophy is the one that became standard in 2026: the spec is the durable, executable artifact, the prompt is disposable. The PM owns the `/spec` (problem, user story, acceptance criteria, out of scope); engineering owns the `/plan` and the `tasks`. The handoff is clean because the spec is structured, not because there's a conversation someone has to decipher.

## How it's used in a session

Each skill is a real command (`.claude/commands/`, see Structure below), not just text to invoke by description. The order follows the PM's full cycle — **reordered 2026-09-17** after auditing how AI-native product teams (Anthropic, OpenAI, Google, Meta) actually sequence this in practice: the prototype moves early, before committing to formal validation or visual identity, instead of being almost the last step. Not every problem uses every skill; you choose based on which one it is:

1. **Discover** — `/discovery`, if the problem is open-ended, gives you the script to understand the business, the flow, and the physical context, and to find the real problem.
2. **Pick a model** — `/monetize`, if it's about monetizing a shared touchpoint, helps you choose between the possible models by weighing the touchpoint owner, the third party who pays, and the end user's friction, with no fixed hierarchy.
3. **Frame the vertical** — `/evaluate`, if it's "should we enter X?", with the platform-vs-specific matrix.
4. **Make the case** — `/business-case` to defend the decision in business terms and resolve build-vs-integrate.
5. **Prioritize** — `/prioritize`, if there are several options, gives the framework with an explicit criterion.
6. **Specify — draft** — `/spec` produces a light EARS spec: the decision already made, turned into something that originates the prototype and, if applicable, the hypothesis that `validate-fast` will fill in. It's not the final version — that comes after `finalize-product-design`, see below.
7. **Prototype** — `/prototype` generates a functional artifact to show the flow instead of describing it. By default it's LOW fidelity (gray/neutral) — doesn't need a fixed visual identity. Validates ONE fast flow, before investing in formal validation or polishing the brand; it's not the final design of the whole product.
8. **Validate what** — if applicable, `/validate` defines the cheapest test that confirms or kills the hypothesis — now against the real prototype that already exists, not just a hypothesis on paper.
9. **Validate how** — if applicable, `/human-validate` is the execution script with real people: asking for commitment instead of opinion, sample size, avoiding false signals. Especially necessary in multi-sided models (touchpoint owner, paying third party, end user). On a solo project with no external users to validate, a direct review by the PM can replace this — it's still a real check, just informal, not one of the 13 skills.

`/design-system` isn't a numbered step in the linear flow, and isn't a prerequisite for every prototype — only for a HIGH-fidelity one (with real branding), and only once the low-fidelity flow has already passed step 8/9 above. Standard order verified (2026-09-17, Nielsen Norman Group and UX process guides): research → low-fidelity flow → high-fidelity visual design, not the other way around. It's invoked once per project, when that high-fidelity version is needed for the first time, and doesn't repeat every session — it's only revisited with a deliberate brand review. If the conversation inside `/prototype` starts circling around palette, typography, or "this doesn't feel differentiated," that's the signal to go back to `/design-system` instead of continuing to iterate there.

`/voice` isn't a numbered step either — it's the equivalent of `/design-system` but for words (verified 2026-09-17, real content-design practice: voice gets locked with actionable Do/Don't rules and real examples, never loose adjectives, and tone varies by context even while the voice stays constant). Without this, copy gets decided on the fly inside `/prototype` — the same drift that already happened with color before `/design-system` existed. It's locked once, only revisited deliberately. Same moment as `/design-system`: after the flow is validated, before investing in the complete inventory.

`/finalize-design` isn't a numbered step in the linear flow either — it comes AFTER `/prototype` (flow validated) and `/design-system`/`/voice` (identity and voice locked), when the complete, final design of every real screen/state is needed, ready for engineering. It's not the same as a high-fidelity prototype: verified (2026-09-17, MEDIUM-STRONG signal) that even within the same design role, a "high-fidelity mockup" (the complete reference) and a "prototype" (the fast validation of a flow) are distinct deliverables. Bundling them was exactly the confusion this separate skill avoids.

**Specify — final version**, after `/finalize-design`: `write-spec` gets invoked again (same skill, second pass) to review and close the spec with what actually got validated and finalized — not with what was expected at the start. This is what `/plan` takes as the durable artifact, along with `/finalize-design`'s inventory when it exists.

`/research` isn't a fixed step in the flow either, but for the opposite reason as `/design-system`: it's invoked ad hoc whenever a market data point is missing in any of the previous steps, and looks it up in the moment instead of assuming. The PM doesn't use `/plan`: it takes the already-finalized spec and the `engineer` agent executes it — and when the project needed `/finalize-design`, it's THAT complete inventory that `/plan` builds from, not the validation prototype.

## Structure

```
.
├── ai-specs/                       # canonical source; .claude/ .codex/ .cursor/ are symlinks into here
│   ├── .agents/        # roles the copilot can adopt
│   ├── .commands/      # real commands: /discovery /monetize /evaluate /business-case
│   │                   # /prioritize /spec /prototype /validate /human-validate
│   │                   # /design-system /voice /finalize-design /research /plan
│   └── skills/         # the reusable flows, one per command (same shape across all 13)
│       ├── discovery-operator/
│       ├── design-monetization-model/
│       ├── evaluate-vertical/
│       ├── business-case/
│       ├── prioritize-roadmap/
│       ├── write-spec/
│       ├── validate-fast/
│       ├── human-validation/
│       ├── establish-design-system/
│       ├── lock-content-voice/
│       ├── build-prototype/
│       ├── finalize-product-design/
│       └── live-research/
├── docs/               # doc_base_standards.md (how the harness itself decides/specifies/
│   │                     # validates/changes, always preloaded) + context, split into
│   │                     # four by data nature:
│   ├── doc_base_standards.md      # the harness's base standards — generic, already complete
│   ├── doc_company_context.md     # stable, preloaded (what the company/product/business is) — template, fill it in before starting
│   ├── doc_market_research.md     # live, dated, refreshed by skills/live-research — template
│   └── doc_open_questions.md      # what we don't know, asked of the team, never invented — template, starts empty
├── specs/               # real /spec output for this project — starts empty
└── README.md
```

`docs/doc_design_system.md` and `docs/doc_voice.md` don't ship in the repo — they're not templates to fill in by hand, they're OUTPUT from `establish-design-system` and `lock-content-voice` (they get created the first time you run those skills). If a skill that needs them can't find them, it'll say so and suggest which one to run first — you don't need to create them yourself.

The principle behind the `docs/` split: what's stable gets preloaded, what changes fast gets looked up in the moment, what we don't know gets asked (never invented), and a design decision gets locked once and reused — not re-decided on every prototype.

## Why this and not a PRD

A thirty-page PRD written before a prototype is waterfall paperwork, not SDD. Here you write the minimum spec that removes ambiguity for the next phase, and validate assumptions early. Acceptance criteria go in condition-behavior format (EARS) because that maps almost one-to-one with test cases, which is exactly what an AI agent or an engineer needs to not have to guess what you meant.

## How to start a new project

1. Use GitHub's **"Use this template"** button to create your own copy (or clone the repo directly).
2. Fill in `docs/doc_company_context.md` with your real company/product context before invoking the first skill — all of them read it as the starting point.
3. Run `/discovery` (or the command that applies if you already have the problem clear — see the table above).

`docs/doc_market_research.md` and `docs/doc_open_questions.md` get populated during the work, not before: the first one via `skills/live-research`, the second by hand whenever a question comes up that only the team can answer. This repo doesn't ship with solved examples or data from any real company — those are specific to each project; each `SKILL.md` describes its own expected output format.

## Real use

This is the harness I use to build my own work — including my professional portfolio, which ran the full flow (discovery → prioritization → spec → prototype → validation) before a single line of the site's code got written. It's not a theoretical exercise.

## Credits

The portable architecture (`ai-specs/` as the canonical source + symlinks to `.claude`/`.cursor`/`.codex`) is adapted from [LIDR-academy/lidr-specboot](https://github.com/LIDR-academy/lidr-specboot) (MIT), a harness built for engineering. The 13 skills and all the methodology content here are an original rewrite for PM work, built with AI assistance (Claude Code) — none of the text is shared with the original.

## License

MIT — see `LICENSE`. Use it, adapt it, keep it.
