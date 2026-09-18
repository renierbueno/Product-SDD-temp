---
name: lock-content-voice
description: Usar cuando hay que fijar (o revisar deliberadamente) la voz, el tono, y el copy real del producto — el equivalente de establish-design-system pero para palabras, no para color. Sin esto, el contenido se decide al vuelo dentro de build-prototype, la misma deriva que ya pasó con paleta y tipografía antes de que existiera establish-design-system. Produce un doc de voz fijado (principios accionables con ejemplos Do/Don't, no adjetivos sueltos) más el copy real de las piezas clave del sitio, cerrado, no una lista abierta de borradores.
---

# Fijar la voz y el contenido

Objetivo: decidir UNA vez cómo suena el producto — y escribir el copy real de las piezas que bloquean el build — no redecidirlo cada vez que se construye un prototipo.

## Cuándo usarla

- Hay contenido real pendiente (un headline vago, una sección que "no suena como yo", texto que todavía no está en su versión final) y bloquea marcar algo FINAL en `finalize-product-design`.
- Alguien dice que algo "no suena humano" o "sí es esto no yo" — esa es la señal de que la conversación se salió de estructura/flujo y entró en voz. Párala y muévela aquí, no la seed dentro de `build-prototype`.
- El producto tiene una voz real ya demostrada en otro lugar (una muestra de escritura real, un voice guide existente) que hay que heredar, no inventar desde cero.

## Qué NO es esta skill

- **No decide identidad visual.** Eso es `establish-design-system`. Esta skill decide palabras, no colores.
- **No decide estructura ni flujo.** Eso ya pasó en `build-prototype`/`prioritize-roadmap`. Esta skill asume que la estructura ya está decidida y escribe el copy que va dentro de ella.
- **No inventa hechos.** Todo dato, cifra o afirmación viene de las mismas fuentes de verdad que ya usa el resto del harness (`doc_company_context.md`, el content-bank del proyecto) — esta skill decide CÓMO se dice, nunca QUÉ se afirma.
- **No es un ejercicio de adjetivos.** "Cálido, directo, cercano" no es una guía de voz — es una lista de deseos. La salida tiene que ser accionable: ejemplos reales Do/Don't, no atributos sueltos (verificado 2026-09-17, práctica real de content design: una guía de voz que no da ejemplos concretos no cambia cómo nadie escribe).

## Insumos (léelos antes de proponer nada)

- Cualquier muestra REAL de escritura del sujeto ya existente (un voice guide, un email real, una respuesta real a una pregunta) — la voz se hereda de ahí, no se inventa. Si no hay ninguna, decirlo explícitamente antes de proponer nada.
- `docs/doc_company_context.md` — quién es la audiencia, qué ya sabe, qué registro necesita (ver discovery si existe una nota sobre esto).
- El feedback real ya dado sobre contenido existente (qué se rechazó y por qué) — es la señal más fuerte de todas, más que cualquier plantilla.

## Proceso

**Paso 1 — Extrae la voz de muestras reales, no la inventes.** Lee el material de voz ya existente línea por línea. Identifica patrones concretos y repetibles: qué palabras evita, cómo abre una frase, cómo cierra, qué tan formal es, dónde mete humor seco vs. dónde no. Cada patrón tiene que señalar a una muestra real, no a una intuición sobre "cómo debería sonar".

**Paso 2 — Convierte cada patrón en una regla Do/Don't con ejemplo.** "Directo" no es una regla. "No abre con una pregunta retórica; dice el hecho primero" con un ejemplo real al lado, sí lo es. Mínimo 5 reglas, cada una con un ejemplo Do y un ejemplo Don't tomado del feedback real ya dado (verificado 2026-09-17, señal FUERTE: una guía de voz sin ejemplos concretos por regla no logra que otros escriban distinto).

**Paso 3 — Mapea tono por contexto, no un tono único para todo.** El mismo producto suena distinto en un headline que en un mensaje de error (verificado 2026-09-17, práctica estándar de content design: la voz es constante, el tono varía por escenario). Enumera los contextos reales del producto (headline, case study, mensaje de error, CTA, meta description) y qué cambia en cada uno.

**Paso 4 — Escribe el copy real de las piezas bloqueadas, cerrado.** No "aquí hay tres versiones del headline" indefinidamente — una decisión final por pieza, con las alternativas descartadas anotadas brevemente (qué se probó, por qué no). Cada pieza de copy tiene que trazarse a un hecho real (`doc_company_context.md`/content-bank) si afirma algo, nunca inventado.

## Salida esperada

```
Reglas de voz (Do/Don't, con ejemplo cada una): [mínimo 5]
Tono por contexto: [headline / case study / error / CTA / meta — qué cambia en cada uno]
Copy fijado — piezas bloqueadas: [cada headline/sección real, versión final, trazable a un hecho si afirma algo]
Qué se descartó y por qué: [breve, por pieza]
Estado: [FIJADO — con fecha — o EN PAUSA / EXPLORADO SIN CERRAR, nunca ambiguo]
```

Guarda el resultado completo en `docs/doc_voice.md`. Si el estado es EN PAUSA, dilo explícitamente.

## Cómo se conecta con el resto

Recibe de `discovery-operator` (registro/nombre ya decidido) y de cualquier muestra de voz real ya existente fuera del harness. Un `build-prototype`/`finalize-product-design` posterior lee `docs/doc_voice.md` en vez de escribir copy nuevo cada vez. `finalize-product-design` no puede marcar una pantalla FINAL si su copy no viene de aquí.

## No está completo si...

- No está completo si las reglas de voz son adjetivos sueltos sin ejemplo Do/Don't.
- No está completo si algún patrón de voz no se puede trazar a una muestra real de escritura del sujeto.
- No está completo si el tono se trató como uno solo para todo el producto, sin variar por contexto.
- No está completo si el copy de una pieza bloqueada afirma algo que no está en `doc_company_context.md` o el content-bank.
- No está completo si queda como varias versiones abiertas sin una decisión final por pieza.
- No está completo si el resultado no se guardó en `docs/doc_voice.md`.
