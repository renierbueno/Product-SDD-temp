---
name: business-case
description: Usar para argumentar una decisión de producto en términos de negocio y defenderla ante Comercial o el Product Director. No asume ningún modelo de ingreso fijo. Produce el caso a favor de una decisión, con el trade-off y el mayor riesgo explícitos.
---

# Argumentar el business case

Objetivo: convertir una decisión de producto en un argumento de negocio que alguien de Comercial o Dirección pueda entender y rebatir, y detectar qué gaps bloquean la entrada a un vertical o modelo nuevo, no solo defender la decisión ya tomada.

Importante: si la empresa está abriendo modelos de negocio nuevos, NO asumas que todo tiene que caber en el modelo actual (`docs/doc_company_context.md`). El punto es justo lo contrario: encontrar el mejor modelo para cada caso. El modelo actual es la base, no una restricción sobre lo nuevo.

## Cuándo usarla

- Ya hay una decisión de producto tomada y hay que defenderla ante Comercial o Dirección.
- Hace falta decidir build vs. integrate y justificarlo en términos de negocio.
- Alguien pregunta "¿cuánto podría mover esto en ingresos?" y hace falta una respuesta con supuestos explícitos, no una cifra suelta.

## El caso, en cinco piezas

```
Decisión: [qué se construye o en qué se entra]

Por qué el negocio lo necesita:
[el problema u oportunidad en términos de dinero o posición, no de features]

Cómo gana dinero (o cómo se sostiene):
[el modelo: suscripción, comisión, rebaja compensada, ingreso de marca, mix.
 Di cuál y por qué encaja mejor que las alternativas. Aquí NO hay respuesta por defecto.]

Qué cuesta y qué arriesga:
[esfuerzo de construir + el riesgo real, incluido el de mantenimiento de plataforma]

Por qué ahora:
[qué lo hace urgente; qué pasa si esperamos]
```

## Las preguntas que Comercial te va a hacer (anticípalas)

- ¿Cuánto podría mover esto en ingresos y en qué plazo? (aunque sea un rango con supuestos)
- ¿Qué clientes/cuentas se desbloquean con esto?
- ¿El cliente/socio lo va a querer, o se lo tenemos que empujar?
- ¿Qué pasa con el margen si el modelo lleva coste variable nuevo?
- ¿Esto nos ata a un proveedor externo? (build vs. integrate)

Ten una respuesta, aunque sea con supuestos marcados, para cada una.

## Build vs. integrate (decisión de negocio, no solo técnica)

Cuando el caso implica una capacidad nueva (motor de campañas, catálogo, settlement, reservas), la pregunta que de verdad decide es: **¿esto toca el activo exclusivo de la empresa (su red, su relación con el cliente, sus datos propios), o es infraestructura genérica que un tercero ya resuelve mejor?**

```
¿Toca el activo exclusivo de la empresa?: [sí / no]
¿Qué existe ya que podríamos integrar? [nombra las opciones reales del mercado]
Coste de integrar: [rápido pero dependencia + margen cedido a un tercero]
Coste de construir: [lento pero es producto propio y diferenciado]
Recomendación: [una] porque [criterio: velocidad de entrada / diferenciación / margen / control del dato]
```

La regla honesta: si toca el activo exclusivo, constrúyelo; si es genérico, integra para entrar rápido y validar, y evalúa build solo si el volumen lo justifica. Di cuál es cuál en este caso.

## Con datos pequeños o supuestos

Presenta los números como escenarios con supuestos visibles, no como proyecciones firmes. "Si asumimos X cuentas y Y de ticket, esto ronda Z" es honesto; una cifra sola parece inventada. Enmarca los hallazgos como indicadores direccionales.

## Salida esperada

Las cinco piezas del caso + la decisión build-vs-integrate si aplica. Corto y defendible. La prueba de un buen caso: alguien de Comercial podría rebatirlo con datos, no con "no me convence".

## Cómo se conecta con el resto

Recibe de `evaluate-vertical` (paso 2b) o `design-monetization-model` cuando el build-vs-integrate es el eje de la decisión. Sigue con `prioritize-roadmap` si hay más opciones sobre la mesa, o directo con `write-spec` si ya está decidido.

## No está completo si...

- No está completo si falta alguna de las cinco piezas del caso.
- No está completo si los números no llevan los supuestos visibles.
- No está completo si implica una capacidad nueva y no se respondió build vs. integrate.
