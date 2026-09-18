---
description: Invokes the lock-content-voice skill to lock voice, tone, and the real locked copy
argument-hint: [which piece of copy is blocked, if there's already an idea]
---

# /voice

Invoke the `lock-content-voice` skill (use the Skill tool with skill: "lock-content-voice") with this context:

$ARGUMENTS

Follow the full process in `ai-specs/skills/lock-content-voice/SKILL.md`: extract the voice from real samples (never invented), turn each pattern into a Do/Don't rule with an example, map tone by context, write the real, closed copy (not open versions), and save the result to `docs/doc_voice.md`.
