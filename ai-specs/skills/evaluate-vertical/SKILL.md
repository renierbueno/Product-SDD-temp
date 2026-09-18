---
name: evaluate-vertical
description: Usar cuando la pregunta es "¿deberíamos entrar en el vertical X?" o "¿qué necesitaría X para correr sobre nuestra plataforma?". Produce una decisión de entrar/no entrar con criterio explícito y un desglose de qué se reutiliza de la plataforma vs. qué es específico del vertical.
---

# Evaluar una vertical nueva

Objetivo: decidir si la empresa debería entrar en un vertical, y si sí, qué se construye una vez como capacidad configurable vs. qué es específico. Este es el ejercicio central de esta función.

## Cuándo usarla

- Te preguntan "¿deberíamos entrar en el vertical X?".
- Necesitas saber qué necesitaría un vertical nuevo para correr sobre la plataforma existente.
- Hay que decidir qué se construye una vez como capacidad configurable vs. qué es específico del vertical.

## Preguntas de arranque (hazlas antes de producir nada)

1. ¿Quién opera este vertical y cuál es su workflow diario?
2. ¿Qué tipo de punto de servicio hay, y qué integración técnica requiere (API, hardware, protocolo propietario, otro)?
3. ¿Qué bloquea hoy la entrada, un gap de producto o un tema comercial?
4. ¿Cuál es el tamaño y la frecuencia de compra del vertical? (define si el modelo de negocio actual aguanta)

## Paso 1 — Perfil del vertical

Rellena:

```
Vertical: [nombre]
Operador tipo: [quién opera el punto de servicio]
Consumidor tipo: [quién paga]
Ticket medio estimado: [€] · Frecuencia: [alta/media/baja]
Integración técnica requerida: [API / hardware propietario / protocolo específico / desconocido]
Por qué ahora: [qué lo hace relevante]
```

## Paso 2 — La matriz plataforma vs. específico (el corazón del análisis)

Para cada necesidad del vertical, clasifícala:

| Necesidad del vertical | ¿Ya existe en la plataforma? | ¿Configurable o build específico? | Justificación |
|---|---|---|---|
| Cobro sin efectivo | Sí | Configurable | Ya es core |
| [ej: sesión por tiempo/uso] | Parcial | Configurable | Ya existe en otro vertical |
| [ej: control de acceso] | No | Evaluar build | Nuevo formato |
| [ej: reserva previa] | No | Evaluar build | Nuevo formato |

Regla: si algo se parece a una capacidad que ya existe para otro vertical, es configurable, no build nuevo. Solo se justifica un build específico cuando la necesidad no tiene análogo en la plataforma.

## Paso 2b — ¿Construir o integrar?

Para cada necesidad que salga como build específico, pregunta antes de asumir que se construye: ¿existe ya algo en el mercado que podríamos integrar para entrar rápido? Integra para validar la entrada; construye solo lo diferenciador y core. Si esto se vuelve el eje de la decisión, encadena con `business-case`.

## Paso 3 — Decisión

```
Recomendación: [ENTRAR / NO ENTRAR / ENTRAR EN FASE 2]
Criterio de decisión: [ingresos / velocidad / riesgo de mantenimiento]
Qué se construiría primero: [la capacidad mínima]
Qué queda fuera de esta fase: [explícito]
Mayor riesgo: [el que mataría la entrada]
Pregunta abierta para Comercial / PM de la plataforma: [una]
```

## Salida esperada

Una tabla plataforma-vs-específico llena + tres frases de recomendación. No más.

## Cómo se conecta con el resto

Si el build-vs-integrate del paso 2b se vuelve el eje de la decisión, sigue con `business-case`. Para especificar la capacidad que se construiría primero, sigue con `write-spec`.

## No está completo si...

- No está completo si alguna fila de la matriz plataforma-vs-específico no tiene justificación.
- No está completo si la recomendación no es ENTRAR / NO ENTRAR / ENTRAR EN FASE 2 con un criterio explícito.
- No está completo si un build específico no pasó por la pregunta de construir vs. integrar (paso 2b).
