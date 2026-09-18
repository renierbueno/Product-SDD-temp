---
name: prioritize-roadmap
description: Usar cuando hay varias opciones sobre la mesa (varias verticales, varios formatos de monetización, varias features) y hay que decidir el orden. Produce una priorización con criterio explícito y una recomendación de una línea, no un debate abierto.
---

# Priorizar el roadmap de expansión

Objetivo: ordenar opciones con un criterio comunicado, no con intuición. El criterio es tan importante como el resultado.

## Cuándo usarla

- Hay varias verticales, formatos o features sobre la mesa y hay que decidir el orden.
- Alguien pide "prioriza esto" sin dar un criterio, y hace falta declarar uno antes de puntuar.
- Hace falta una recomendación cerrada, no un debate abierto.

## Paso 0 — Fija el criterio antes de puntuar

Pregunta o declara: ¿priorizamos por impacto en ingresos, por velocidad de entrega, o por reducción de riesgo de mantenimiento de plataforma? Escríbelo arriba de todo. Cambiar el criterio cambia el orden, así que se decide primero.

## Paso 1 — RICE (o el marco que aplique)

| Opción | Reach | Impact (1-3) | Confidence (%) | Effort (pers-sem) | Score |
|---|---|---|---|---|---|
| A | | | | | |
| B | | | | | |
| C | | | | | |

Score = (Reach × Impact × Confidence) / Effort.

Di en voz alta el supuesto de cada celda. Con poca información, marca la Confidence baja en vez de inventar Reach.

## Variante: si el criterio es riesgo de mantenimiento

Cuando el criterio dominante es no romper la plataforma, sustituye Impact por "reutilización de plataforma":

| Opción | % reutiliza la plataforma | Builds específicos que exige | Deuda de mantenimiento | Prioridad |
|---|---|---|---|---|

Lo que más reutiliza y menos builds únicos exige sube, aunque su impacto comercial no sea el mayor. Esto respeta el principio de no crear un mosaico de builds inmantenibles.

## Paso 2 — Recomendación

```
Primero: [opción] porque [criterio].
Segundo: [opción].
No ahora: [opción] porque [razón, normalmente riesgo o effort desproporcionado].
Supuesto que más movería este orden si cambia: [uno].
```

## Salida esperada

Tabla + tres líneas de recomendación cerrada. Nunca dejes la decisión abierta "para discutir"; da tu recomendación y di qué la cambiaría.

## Cómo se conecta con el resto

Recibe de `business-case` o `evaluate-vertical` cuando ya hay varias opciones evaluadas por separado. Sigue con `write-spec` para la opción que queda primero.

## No está completo si...

- No está completo si el criterio no se declaró antes de puntuar.
- No está completo si alguna celda de Confidence está inventada en vez de marcada baja por falta de información.
- No está completo si la recomendación queda abierta "para discutir" en vez de cerrada.
