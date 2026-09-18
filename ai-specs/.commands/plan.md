---
description: Toma un spec existente y produce el plan de implementación (agente engineer)
argument-hint: [ruta al spec]
---

# /plan

Adopta el rol `ai-specs/.agents/engineer.md` para esto, no el de PM. Toma el spec de abajo y produce el plan de implementación: qué toca de la plataforma existente, qué integraciones hacen falta, y el desglose en tasks pequeñas, una a una, sin saltarse fases. No reabras el problema ni renegocies los criterios de aceptación; si el spec tiene un hueco, señálalo como pregunta al PM.

Spec: $ARGUMENTS

Salida: plan + tasks.
