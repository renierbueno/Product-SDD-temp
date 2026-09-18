---
description: Invoca la skill finalize-product-design para producir el diseño completo y definitivo de cada pantalla/estado
argument-hint: [alcance del inventario a finalizar, si ya hay una idea]
---

# /finalize-design

Invoca la skill `finalize-product-design` (usa la tool Skill con skill: "finalize-product-design") con este contexto:

$ARGUMENTS

Sigue el proceso completo de `ai-specs/skills/finalize-product-design/SKILL.md`: enumera el inventario completo de pantallas/estados sin dejar nada implícito, aplica `docs/doc_design_system.md` exhaustivamente sin decisiones de identidad nuevas, cubre feliz/error/borde por cada pantalla FINAL, y marca cualquier cosa diferida con su razón.
