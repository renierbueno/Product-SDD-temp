---
name: live-research
description: Usar cuando falta un dato durante una sesión y hay que buscarlo en el momento. Cubre cinco tipos de dato de mercado (tamaño del vertical, comparables de monetización, regulación, benchmarks de precio, comportamiento de usuario), no solo competidores. Es para contexto VIVO que no vive en docs. Produce hallazgos estructurados de forma que el resto del harness los pueda consumir, siempre marcados como señal direccional.
---

# Investigación en vivo

Objetivo: traer datos que no tenemos precargados, en el momento, sin romper el resto del flujo. El principio del harness es que el contexto estable vive en `docs/` y el contexto vivo se busca. Esta skill es el "se busca", y cubre más que competidores.

## Cuándo usarla

Úsala para cualquiera de las cinco categorías de abajo. NO la uses para datos internos de la empresa/proyecto (métricas propias, ICP real, churn): eso no se busca, se PREGUNTA al equipo, va a `doc_open_questions.md`. NO la uses tampoco para releer algo que ya está en `docs/doc_company_context.md` o `docs/doc_market_research.md`; primero mira si ya lo tienes.

## Las cinco categorías, y qué decisión alimenta cada una

**1. Tamaño y crecimiento del vertical concreto**
No es lo mismo el tamaño de la categoría general que el tamaño del vertical concreto que te están preguntando (cuántos actores hay, si el sector crece o se estanca, qué tan fragmentado está entre muchos operadores pequeños o pocas cadenas grandes).
Pregunta tipo: "tamaño mercado [vertical] [país] [año]", "número de operadores [sector] fragmentación [región]".
Alimenta: `evaluate-vertical` (decisión de entrar o no) y `prioritize-roadmap` (el Reach de un RICE).

**2. Comparables de monetización**
Quién ya hace algo parecido y cómo lo cobra.
Pregunta tipo: "quién monetiza algo parecido a [touchpoint] en [contexto]", "modelo de ingresos [comparable]".
Alimenta: `design-monetization-model` (qué modelos existen) y `business-case` (precedente para defender la decisión).

**3. Regulación específica del vertical o del modelo**
La categoría que más se salta la gente y la que más rápido delata a alguien que no ha pensado el problema del todo. Cualquier modelo que segmente por comportamiento o ubicación toca protección de datos. Ciertas categorías de producto o servicio tienen restricciones propias.
Pregunta tipo: "regulación protección de datos publicidad segmentada ubicación", "normativa [vertical] [país]".
Alimenta: `evaluate-vertical` (Paso 2b, build vs. integrate) y `business-case` (qué arriesga).

**4. Benchmarks de precio unitario**
Sin esto, cualquier proyección de ingresos en `business-case` es una cifra inventada. Necesitas el ancla: cuánto vale un CPM comparable, cuánto es una comisión típica del sector, cuánto paga alguien por captar un contacto o una conversión similar.
Pregunta tipo: "CPM medio [formato] [país]", "comisión típica [sector]".
Alimenta: `business-case` (el escenario de ingresos con supuestos visibles) directamente, no se puede escribir ese bloque sin esto.

**5. Comportamiento de usuario en ese tipo de contexto**
Datos de industria sobre cómo reacciona la gente a un formato, no una opinión tuya. Tasas de escaneo de QR en punto físico, tasas de conversión de pantallas interactivas, cuánto tiempo de atención capta un formato comparable.
Pregunta tipo: "tasa de conversión [formato/canal] benchmark", "tiempo de atención [formato] benchmark".
Alimenta: `design-monetization-model` (el eje fricción-vs-momento deja de ser intuición y se vuelve argumento).

Todas alimentan también `human-validation`: un benchmark de industria es el umbral con el que comparas tu propia señal cuando valides con personas reales.

## Cómo buscar sin perder la sesión

1. **Una pregunta concreta por búsqueda**, dentro de una sola categoría de las cinco. No mezcles "tamaño de mercado y regulación" en una búsqueda.
2. **Antes de buscar, decide qué decisión cambia.** Si el dato no mueve una decisión de la sesión, no lo busques.
3. **Máximo 2 o 3 búsquedas por pregunta.** Si no aparece, di que no hay dato público claro y sigue con el supuesto marcado.
4. **Prioriza fuente original** (informe sectorial, regulador, web de la empresa comparable) sobre agregadores.
5. **Casos de fracaso también cuentan**, no solo de éxito. Busca activamente si algún comparable de la categoría 2 falló o se retiró.

## Regla de honestidad (la más importante)

- Un comparable no es una validación. Prueba que alguien lo hace, no que funcione aquí.
- Muestra de una o dos empresas por vertical = señal direccional, nunca conclusión.
- Nunca inventes una cifra para llenar un hueco, ni de mercado ni de precio. Si no hay dato público, el output es "no hay dato público fiable, esto queda como pregunta para el equipo".
- No mezcles dato externo (esto se busca) con dato interno de la empresa/proyecto (esto se pregunta). Si la pregunta es sobre la propia empresa, no es tarea de esta skill, va a `doc_open_questions.md`.

## Cómo comunicarlo

Verbaliza el estado del dato en el momento en que lo buscas, no lo escondas dentro de la respuesta final: "este dato no lo tengo precargado porque cambia rápido, así que lo busco ahora." Y, según la categoría: "encontré [X], pero es una sola empresa, así que lo tomo como dirección, no como prueba" (categoría 2 o 5), o "sin un benchmark de precio no puedo dar una cifra de ingreso responsable, así que lo busco antes de proponer un número" (categoría 4), o "antes de proponer este modelo, tendría que confirmar si hay alguna restricción regulatoria, lo miro ahora" (categoría 3).

## Salida esperada

```
Categoría: [1-5, de la lista de arriba]
Pregunta que responde: [la decisión que estaba bloqueada]
Hallazgo: [el dato, en una frase]
Fuente y fecha: [de dónde, cuándo]
Tamaño de la evidencia: [una empresa / un informe / patrón repetido en varias]
Fuerza de la señal: [FUERTE si varias fuentes coinciden / DÉBIL si es un solo caso]
Qué decisión cambia: [cómo afecta a la sesión]
Supuesto que quedaría si esto es cierto: [lo que asumes a partir de aquí, tagueado para validar con el equipo]
```

## Cómo se conecta con el resto

- Categorías 1 y 3 → `evaluate-vertical`.
- Categoría 2 → `design-monetization-model` y `business-case`.
- Categoría 4 → `business-case`, obligatorio antes de dar cualquier cifra de ingreso.
- Categoría 5 → `design-monetization-model`, y de ancla para `human-validation`.
- Un supuesto que confirmas o tumbas se actualiza verbalmente en la sesión; NO se reescribe `docs/doc_market_research.md` en caliente, el doc es contexto estable con fecha, la sesión es efímera.

## No está completo si...

- No está completo si el hallazgo no dice tamaño de la evidencia y fuerza de la señal.
- No está completo si mezcla dato externo con dato interno de la empresa/proyecto.
- No está completo si se buscó sin que hubiera una decisión concreta bloqueada por ese dato.
