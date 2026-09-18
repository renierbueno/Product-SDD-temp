---
description: Invoca la skill lock-content-voice para fijar voz, tono, y el copy real bloqueado
argument-hint: [qué pieza de copy está bloqueada, si ya hay una idea]
---

# /voice

Invoca la skill `lock-content-voice` (usa la tool Skill con skill: "lock-content-voice") con este contexto:

$ARGUMENTS

Sigue el proceso completo de `ai-specs/skills/lock-content-voice/SKILL.md`: extrae la voz de muestras reales (nunca inventada), convierte cada patrón en una regla Do/Don't con ejemplo, mapea el tono por contexto, escribe el copy real cerrado (no versiones abiertas), y guarda el resultado en `docs/doc_voice.md`.
