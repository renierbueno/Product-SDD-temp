---
description: Invokes the finalize-product-design skill to produce the complete, final design of every screen/state
argument-hint: [scope of the inventory to finalize, if there's already an idea]
---

# /finalize-design

Invoke the `finalize-product-design` skill (use the Skill tool with skill: "finalize-product-design") with this context:

$ARGUMENTS

Follow the full process in `ai-specs/skills/finalize-product-design/SKILL.md`: list the complete inventory of screens/states without leaving anything implicit, apply `docs/doc_design_system.md` exhaustively with no new identity decisions, cover happy/error/edge for every FINAL screen, and mark anything deferred with its reason.
