---
name: write-spec
description: Use to produce the artifact that gets handed off to engineering. Turns a product decision into an executable spec with acceptance criteria in EARS format and an explicit out-of-scope block.
---

# Write the spec (spec-driven development)

Goal: produce the artifact engineering can pick up and execute without a clarification meeting. The PM owns this; engineering owns the plan and the tasks that come out of it.

**This skill runs twice, not once (reordered 2026-09-17 after auditing the real practice of AI-native teams).** First pass: a light draft, right after `prioritize-roadmap`, that originates the prototype and (if applicable) the hypothesis `validate-fast` fills in — it's not the final version, and it doesn't need to be yet. Second pass: after `finalize-product-design`, the same spec gets reviewed and closed with what actually got validated and finalized, not what was expected at the start. `/plan` takes this second version, not the first.

## When to use it

- **First pass:** a product decision has already been made (from `design-monetization-model`, `evaluate-vertical`, or `prioritize-roadmap`) and it's time to turn it into something that originates a prototype and, if applicable, a hypothesis for `validate-fast`.
- **Second pass:** the flow is already validated, the visual identity and voice are already locked (if the project needed them), and `finalize-product-design` already produced the complete inventory — time to close the spec with the final truth before handing it to `/plan`.
- You need measurable acceptance criteria, not a prose description.
- You need to explicitly state what does NOT get built in this version.

## Template

```markdown
# Spec: [short feature name]

## Context
[2-3 sentences: what problem it solves and for whom. No embedded solution.]

## User story
As a [specific user type],
I want [action],
so that [measurable outcome].

## Acceptance criteria (EARS)
- WHEN [event] THE SYSTEM SHALL [observable behavior]
- WHEN [event] THE SYSTEM SHALL [observable behavior]
- IF [edge condition] THEN THE SYSTEM SHALL [behavior]
- IF [error case] THEN THE SYSTEM SHALL [error handling]
- WHILE [ongoing state] THE SYSTEM SHALL [behavior]

## Out of scope (this version)
- [thing that does NOT get built]
- [thing that does NOT get built]

## Dependencies / integrations
- [e.g.: requires the backoffice to expose X] · [e.g.: depends on an external provider for Y]
- Does this integrate with something external that already exists, or does it get built in-house? [decide and justify; if it's a big business decision, take it to business-case]

## Definition of "done"
- All EARS criteria pass as test cases
- [metric that will move] instrumented and visible in the backoffice/analytics

## How it's validated before scaling
[link to the validate-fast skill: the cheapest test that confirms the hypothesis]
```

## Rules for writing the criteria

- No adjectives ("fast", "easy", "intuitive"). Only behavior that can be observed and tested.
- One criterion = one behavior. If a line has an "and," split it in two.
- Always cover: the happy path, at least one edge case, and at least one error case.
- If you can't test it, it's not an acceptance criterion; it's a wish. Rewrite it.

## Why EARS

Condition-behavior criteria map almost one-to-one with test cases. That's what lets an engineer or an AI agent implement against the spec without having to interpret you. The handoff is clean because the artifact is structured, not a conversation someone has to decipher.

## Expected output

The markdown above, filled in, for the specific feature. Short and executable.

## How it connects with the rest

Receives from any skill that produced a product decision (`design-monetization-model`, `evaluate-vertical`, `prioritize-roadmap`). In the first pass, follow with `build-prototype` (the spec originates the prototype, not the other way around) and, if applicable, `validate-fast` for the "how it's validated" section. In the second pass, receives from `finalize-product-design` and feeds directly into `/plan`.

## Not complete if...

- Not complete if any acceptance criterion uses a non-measurable adjective ("fast", "easy", "intuitive").
- Not complete if the out-of-scope block is missing.
- Not complete if any EARS criterion can't be turned directly into a test case.
- Not complete if the "how it's validated before scaling" section is missing (or if that section is still unresolved in the second pass, when it should already be closed).
- Not complete if the second pass still describes what was expected at the start instead of what actually got validated and finalized.
