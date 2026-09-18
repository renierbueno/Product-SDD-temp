---
name: write-spec
description: Usar para producir el artefacto que se entrega a ingeniería. Convierte una decisión de producto en un spec ejecutable con criterios de aceptación en formato EARS y fuera de alcance explícito.
---

# Escribir el spec (spec-driven development)

Objetivo: producir el artefacto que ingeniería puede tomar y ejecutar sin una reunión de aclaración. El PM es dueño de esto; ingeniería es dueña del plan y las tasks que salen de aquí.

**Esta skill corre dos veces, no una (reordenado 2026-09-17 tras auditar la práctica real de equipos AI-native).** Primera pasada: un borrador ligero, justo después de `prioritize-roadmap`, que origina el prototipo y (si aplica) la hipótesis que `validate-fast` rellena — no es la versión final, y no hace falta que lo sea todavía. Segunda pasada: después de `finalize-product-design`, se revisa y se cierra el mismo spec con lo que realmente quedó validado y finalizado, no con lo que se esperaba al principio. `/plan` toma esta segunda versión, no la primera.

## Cuándo usarla

- **Primera pasada:** ya hay una decisión de producto tomada (de `design-monetization-model`, `evaluate-vertical` o `prioritize-roadmap`) y toca convertirla en algo que origine un prototipo y, si aplica, una hipótesis para `validate-fast`.
- **Segunda pasada:** el flujo ya se validó, la identidad visual y la voz ya están fijadas (si el proyecto las necesitó), y `finalize-product-design` ya produjo el inventario completo — toca cerrar el spec con la verdad final antes de pasarlo a `/plan`.
- Necesitas criterios de aceptación medibles, no una descripción en prosa.
- Hace falta declarar explícitamente qué NO se construye en esta versión.

## Plantilla

```markdown
# Spec: [nombre corto de la feature]

## Contexto
[2-3 frases: qué problema resuelve y para quién. Sin solución embebida.]

## Historia de usuario
Como [tipo de usuario concreto],
quiero [acción],
para [resultado medible].

## Criterios de aceptación (EARS)
- WHEN [evento] THE SYSTEM SHALL [comportamiento observable]
- WHEN [evento] THE SYSTEM SHALL [comportamiento observable]
- IF [condición de borde] THEN THE SYSTEM SHALL [comportamiento]
- IF [caso de error] THEN THE SYSTEM SHALL [manejo del error]
- WHILE [estado continuo] THE SYSTEM SHALL [comportamiento]

## Fuera de alcance (esta versión)
- [cosa que NO se construye]
- [cosa que NO se construye]

## Dependencias / integraciones
- [ej: requiere que el backoffice exponga X] · [ej: depende de un proveedor externo para Y]
- ¿Esto se integra con algo externo que ya existe, o se construye en propio? [decide y justifica; si es una decisión de negocio grande, sácala a business-case]

## Definición de "hecho"
- Todos los criterios EARS pasan como casos de prueba
- [métrica que se moverá] instrumentada y visible en el backoffice/analítica

## Cómo se valida antes de escalar
[enlaza a la skill validate-fast: la prueba más barata que confirma la hipótesis]
```

## Reglas de escritura de los criterios

- Nada de adjetivos ("rápido", "fácil", "intuitivo"). Solo comportamiento que se puede observar y testear.
- Un criterio = un comportamiento. Si una línea tiene un "y", pártela en dos.
- Cubre siempre: el camino feliz, al menos un caso de borde, y al menos un caso de error.
- Si no puedes testearlo, no es un criterio de aceptación; es un deseo. Reescríbelo.

## Por qué EARS

Los criterios en condición-comportamiento mapean casi uno a uno con casos de prueba. Eso es lo que permite que un ingeniero o un agente de IA implemente contra el spec sin tener que interpretarte. El handoff es limpio porque el artefacto es estructurado, no una conversación que hay que descifrar.

## Salida esperada

El markdown de arriba, lleno, para la feature concreta. Corto y ejecutable.

## Cómo se conecta con el resto

Recibe de cualquier skill que produjo una decisión de producto (`design-monetization-model`, `evaluate-vertical`, `prioritize-roadmap`). En la primera pasada, sigue con `build-prototype` (el spec origina el prototipo, no al revés) y, si aplica, con `validate-fast` para la sección "cómo se valida". En la segunda pasada, recibe de `finalize-product-design` y alimenta directamente `/plan`.

## No está completo si...

- No está completo si algún criterio de aceptación usa un adjetivo no medible ("rápido", "fácil", "intuitivo").
- No está completo si falta el bloque de fuera de alcance.
- No está completo si algún criterio EARS no se puede convertir directamente en un caso de prueba.
- No está completo si falta la sección de cómo se valida antes de escalar (o si esa sección quedó sin resolver en la segunda pasada, cuando ya debería estar cerrada).
- No está completo si la segunda pasada todavía describe lo que se esperaba al principio en vez de lo que realmente quedó validado y finalizado.
