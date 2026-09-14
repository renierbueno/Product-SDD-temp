---
name: evaluate-vertical
description: Usar cuando la pregunta es "¿deberíamos entrar en el vertical X?" o "¿qué necesitaría X para correr sobre nuestra plataforma?". Produce una decisión de entrar/no entrar con criterio explícito y un desglose de qué se reutiliza de la plataforma vs. qué es específico del vertical.
---

# Evaluar una vertical nueva

Objetivo: decidir si la empresa debería entrar en un vertical, y si sí, qué se construye una vez como capacidad configurable vs. qué es específico. Este es el ejercicio central del rol.

## Preguntas de arranque (hazlas antes de producir nada)

1. ¿Quién es el operador de este vertical y cuál es su workflow diario?
2. ¿Qué tipo de máquina o punto de servicio hay, y qué protocolo de pago usa (MDB, Executive, Validador, otro)?
3. ¿Qué bloquea hoy la entrada, un gap de producto o un tema comercial?
4. ¿Cuál es el tamaño y la frecuencia de compra del vertical? (define si el modelo de cuota fija sin comisión aguanta)

## Paso 1 — Perfil del vertical

Rellena:

```
Vertical: [nombre]
Operador tipo: [quién opera las máquinas]
Consumidor tipo: [quién paga]
Ticket medio estimado: [€] · Frecuencia: [alta/media/baja]
Protocolo de pago de la máquina: [MDB / Executive / Validador / desconocido]
Por qué ahora: [qué lo hace relevante]
```

## Paso 2 — La matriz plataforma vs. específico (el corazón del análisis)

Para cada necesidad del vertical, clasifícala:

| Necesidad del vertical | ¿Ya existe en Space/Spot? | ¿Configurable o build específico? | Justificación |
|---|---|---|---|
| Cobro sin efectivo | Sí | Configurable | Ya es core |
| [ej: sesión por tiempo/count-up] | Parcial | Configurable | Ya existe en lavandería |
| [ej: control de acceso físico] | No | Evaluar build | Nuevo formato |
| [ej: reserva previa] | No | Evaluar build | Nuevo formato |

Regla: si algo se parece a una capacidad que ya existe para otro vertical (ej. count-up de lavandería ≈ over-stay de EV), es configurable, no build nuevo. Solo se justifica un build específico cuando la necesidad no tiene análogo en la plataforma.

## Paso 2b — ¿Construir o integrar?

Para cada necesidad que salga como build específico, pregunta antes de asumir que se construye: ¿existe ya algo en el mercado que podríamos integrar para entrar rápido? Integra para validar la entrada; construye solo lo diferenciador y core. Si esto se vuelve el eje de la decisión, encadena con `business-case`.

## Paso 3 — Decisión

```
Recomendación: [ENTRAR / NO ENTRAR / ENTRAR EN FASE 2]
Criterio de decisión: [ingresos / velocidad / riesgo de mantenimiento]
Qué se construiría primero: [la capacidad mínima]
Qué queda fuera de esta fase: [explícito]
Mayor riesgo: [el que mataría la entrada]
Pregunta abierta para Comercial / PM de Space: [una]
```

## Salida esperada

Una tabla plataforma-vs-específico llena + tres frases de recomendación. No más. Si hay tiempo, encadena con la skill `write-spec` para la capacidad que se construiría primero.
