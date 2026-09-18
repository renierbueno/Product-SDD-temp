---
name: finalize-product-design
description: Usar cuando el flujo crítico ya está validado (build-prototype), la identidad visual ya está fijada (establish-design-system), y la voz/copy ya está fijada (lock-content-voice), y toca producir el diseño completo y definitivo de TODAS las pantallas y estados reales del producto — no una validación rápida de un flujo, sino la referencia exhaustiva que ingeniería va a construir. No requiere que cada pantalla tenga su propio prototipo (eso no es práctica estándar), pero cada pantalla que no lo tuvo debe justificar qué patrón ya validado reutiliza, llevar el porqué real, y pasar un chequeo de viabilidad antes de marcarse FINAL.
---

# Finalizar el diseño del producto

Objetivo: producir el diseño completo y pulido de cada pantalla y cada estado real del producto — el artefacto definitivo, no otra validación. Investigación real (2026-09-17, señal MEDIA-FUERTE): incluso dentro de un solo rol de diseño, "mockup de alta fidelidad" y "prototipo" se listan como entregables DISTINTOS — un prototipo es una herramienta de validación (rápida, desechable, cubre un flujo), un mockup/diseño final es la referencia completa que ingeniería construye.

## Cuándo usarla

- El flujo crítico ya se validó (`build-prototype`, baja o alta fidelidad), la identidad visual ya está `FIJADO` en `docs/doc_design_system.md`, y la voz/copy ya está `FIJADO` en `docs/doc_voice.md` (si el proyecto tiene esa skill corrida — no todo proyecto la necesita).
- Hay un inventario real de pantallas/estados que necesitan diseño final, no solo el flujo de ejemplo que ya se prototipó.
- Esto está a punto de pasar a `/plan` (ingeniería) y hace falta la referencia definitiva, no "el prototipo de la home nada más".

**No hace falta prototipar cada pantalla una por una — eso no es práctica estándar (verificado 2026-09-17, señal FUERTE: la recomendación real es prototipar solo los flujos críticos/de riesgo, 5-15 pantallas según complejidad, no el inventario completo).** La coherencia del resto viene de reutilizar los mismos componentes y patrones ya validados, nunca de inventar algo nuevo sin pasar por `build-prototype` primero. Por eso el Paso 2 de abajo exige nombrar el patrón reutilizado para cada pantalla que no tuvo su propio prototipo — si no se puede nombrar uno real, esa pantalla sí necesita pasar por `build-prototype` antes de entrar aquí.

## Qué NO es esta skill

- **No reemplaza `build-prototype`.** La validación de flujo sigue pasando ahí primero, rápido y desechable, para los flujos críticos. Esta skill asume que esa validación ya ocurrió donde hacía falta.
- **No decide identidad visual.** Aplica `docs/doc_design_system.md` exhaustivamente; no inventa paleta, tipografía, ni motivo de layout nuevo. Si hace falta una decisión de identidad que el sistema fijado no cubre, esa es señal de volver a `establish-design-system`, no de decidirla aquí.
- **No es más iteración de "cómo se ve".** Para cuando esta skill corre, esa pregunta ya está cerrada. Esto es sobre COBERTURA (cada pantalla, cada estado real), no sobre más dirección.
- **No inventa contenido.** El copy tiene que estar en su versión final (voz, posicionamiento, wording), fijado en `docs/doc_voice.md`, antes de entrar aquí — si no lo está, esa es `lock-content-voice` (`/voice`), no un hueco que se rellena al vuelo dentro de esta.

## Proceso

**Paso 1 — Inventario explícito, nada implícito.** Enumera cada pantalla y cada estado real del producto, no solo "la home". Ejemplo del nivel de detalle: no "página de casos", sino "Catálogo: 4 páginas de detalle (o una plantilla + 4 variantes de contenido), estado con imagen / estado solo-texto". Todo lo que no se diseñe en esta pasada se marca DIFERIDO con la razón, nunca se omite en silencio.

**Paso 2 — Para cada pantalla sin prototipo propio, nombra el patrón que reutiliza.** "Reutiliza la tarjeta de listado ya validada en `checkout-hifi-b`" es una justificación real; "se ve parecido" no lo es. Si no hay un patrón real que nombrar, esa pantalla no está lista para esta skill — vuelve a `build-prototype` primero.

**Paso 3 — Aplica el sistema fijado, no lo reinventes.** Cada pantalla reutiliza los mismos tokens/tipografía/motivo de `docs/doc_design_system.md`, y el copy de `docs/doc_voice.md` tal cual esté fijado ahí. Cero decisiones de identidad o de voz nuevas.

**Paso 4 — Cubre los estados reales de cada pantalla, no solo el camino feliz.** Mismo estándar que `build-prototype` (feliz + error + borde), pero ahora para el inventario completo, no un solo flujo.

**Paso 5 — Di por qué existe cada pantalla, no solo qué contiene.** Una frase por pantalla: qué problema real del usuario resuelve, trazable al discovery/`doc_company_context.md` (verificado 2026-09-17: práctica real de equipos de diseño — el archivo de diseño lleva el problema y el porqué, no solo el visual, para que la decisión se pueda auditar después sin adivinar).

**Paso 6 — Chequeo de viabilidad antes de fijar FINAL.** ¿Esta pantalla depende de algo que no existe todavía (un screenshot real, una integración, un dato)? Si sí, es DIFERIDA con esa razón explícita, nunca FINAL con un placeholder disfrazado (verificado 2026-09-17: práctica real — el handoff revisa viabilidad técnica, no solo precisión visual, antes de dar algo por terminado).

## Salida esperada

```
Inventario de pantallas/estados: [lista completa, cada una FINAL o DIFERIDA + razón]
Patrón reutilizado (si no tuvo prototipo propio): [cuál, y de dónde — nunca "se ve parecido"]
Sistema aplicado: [confirma que viene de docs/doc_design_system.md, sin decisiones nuevas]
Copy aplicado: [confirma que viene de docs/doc_voice.md, sin copy nuevo]
Estados cubiertos por pantalla: [feliz / error / borde, por cada una FINAL]
Por qué existe (por pantalla): [el problema real que resuelve, trazable al discovery]
Viabilidad: [qué depende de algo que no existe todavía, y por eso quedó DIFERIDA]
Qué queda fuera de esta pasada: [explícito, con razón — nunca silencioso]
```

Guarda el resultado (o el puntero a los artifacts reales) donde el proyecto guarde sus prototipos — mismo criterio que `build-prototype`.

## Cómo se conecta con el resto

Recibe de `build-prototype` (flujos críticos ya validados), `establish-design-system` (identidad ya fijada, `docs/doc_design_system.md`), y `lock-content-voice` (copy ya cerrado, `docs/doc_voice.md`). Sigue con la segunda pasada de `write-spec` (reordenado 2026-09-17): el spec se cierra aquí, con lo que realmente quedó finalizado, antes de pasar a `/plan` — no directamente de esta skill a `/plan`. `/plan` toma el spec ya cerrado como artefacto durable, y el inventario de esta skill como la referencia real que el agente `engineer` construye, no el prototipo de validación. Una vez construido de verdad, verificar que lo construido coincide con esto (Design QA) es un chequeo real y distinto que este harness todavía no tiene como skill propia — pendiente de decidir si hace falta una, no asumido ni resuelto aquí.

## No está completo si...

- No está completo si el inventario de pantallas/estados no es explícito — cualquier cosa implícita o "sobreentendida" no cuenta.
- No está completo si algo se dejó fuera sin decir explícitamente que está diferido y por qué.
- No está completo si se tomó una decisión de identidad visual nueva dentro de esta skill — esa es señal de volver a `establish-design-system`.
- No está completo si se escribió copy nuevo dentro de esta skill en vez de usar `docs/doc_voice.md` tal cual — esa es señal de volver a `lock-content-voice`.
- No está completo si el contenido de alguna pantalla no está en su versión final.
- No está completo si alguna pantalla marcada FINAL solo cubre el camino feliz.
- No está completo si una pantalla sin prototipo propio no nombra un patrón real que reutiliza.
- No está completo si alguna pantalla no dice qué problema real resuelve.
- No está completo si algo se marcó FINAL sin pasar el chequeo de viabilidad.
