---
name: write-spec
description: Usar para producir el artefacto que se entrega a ingeniería. Convierte una decisión de producto en un spec ejecutable con criterios de aceptación en formato EARS y fuera de alcance explícito. Este es el "asset" que probablemente evalúa la prueba.
---

# Escribir el spec (spec-driven development)

Objetivo: producir el artefacto que ingeniería puede tomar y ejecutar sin una reunión de aclaración. El PM es dueño de esto; ingeniería es dueña del plan y las tasks que salen de aquí.

## Plantilla

```markdown
# Spec: [nombre corto de la feature]

## Contexto
[2-3 frases: qué problema resuelve y para quién. Sin solución embebida.]

## Historia de usuario
Como [operador / consumidor / marca anunciante],
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
- [ej: requiere que Space exponga X] · [ej: depende del PSP de fondo para Y]
- ¿Esto se integra con algo externo que ya existe, o se construye en propio? [decide y justifica; si es una decisión de negocio grande, sácala a business-case]

## Definición de "hecho"
- Todos los criterios EARS pasan como casos de prueba
- [métrica que se moverá] instrumentada y visible en Space

## Cómo se valida antes de escalar
[enlaza a la skill validate-fast: la prueba más barata que confirma la hipótesis]
```

## Reglas de escritura de los criterios

- Nada de adjetivos ("rápido", "fácil", "intuitivo"). Solo comportamiento que se puede observar y testear.
- Un criterio = un comportamiento. Si una línea tiene un "y", pártela en dos.
- Cubre siempre: el camino feliz, al menos un caso de borde, y al menos un caso de error.
- Si no puedes testearlo, no es un criterio de aceptación; es un deseo. Reescríbelo.

## Por qué EARS (dilo si te preguntan)

Los criterios en condición-comportamiento mapean casi uno a uno con casos de prueba. Eso es lo que permite que un ingeniero o un agente de IA implemente contra el spec sin tener que interpretarte. El handoff es limpio porque el artefacto es estructurado, no una conversación que hay que descifrar.

## Salida esperada

El markdown de arriba, lleno, para la feature concreta. Corto y ejecutable. Si te dan tiempo, encadena con `build-prototype` para mostrar el flujo.
