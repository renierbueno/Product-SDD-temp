# Estándares base

Principios que gobiernan cualquier trabajo en este repo. El copiloto los respeta siempre.

## Cómo se decide

- **Criterio explícito, siempre.** Ninguna priorización sin decir en base a qué (impacto en ingresos, velocidad de entrega, riesgo de mantenimiento). Se comunica el criterio, no solo el resultado.
- **Supuestos en voz alta.** Cuando falta información, se asume lo mínimo necesario para avanzar y se marca como [SUPUESTO — validar]. No se pide más info de la necesaria.
- **Plataforma vs. específico.** Toda feature de una vertical pasa por la pregunta: ¿esto se construye una vez como capacidad configurable, o es genuinamente específico de este vertical? Se justifica la respuesta.
- **Findings como indicadores.** Con datos pequeños, los hallazgos se presentan como señales direccionales, no como conclusiones definitivas.

## Cómo se especifica

- **El spec es el artefacto durable, el prompt es desechable.** Todo lo que se vaya a construir de verdad pasa por un spec.
- **Criterios de aceptación en formato EARS.** Patrones: `WHEN [evento] THE SYSTEM SHALL [comportamiento]`, `IF [condición] THEN [comportamiento]`, `WHILE [estado] THE SYSTEM SHALL [comportamiento]`. Nada de adjetivos ("rápido", "intuitivo") como criterio; solo comportamiento medible.
- **Fuera de alcance explícito.** Todo spec declara qué NO se construye en esta versión.
- **Mínimo viable de spec.** Se escribe lo justo para eliminar ambigüedad de la siguiente fase, no un PRD de treinta páginas antes de validar nada.

## Cómo se valida

- **La prueba más barata primero.** Antes de comprometer ingeniería, se define la validación más rápida que confirma o mata la hipótesis.
- **El PM valida antes de entregar.** Cuando se puede, se prototipa con IA para no hacer perder tiempo a ingeniería en algo con un problema obvio de UX o alcance.
- **Un número por hipótesis.** Cada spec dice qué métrica confirmaría que funcionó.

## Tono de escritura

Simple, directo, humano. Sin buzzwords, sin lenguaje que suene a IA. Sin guiones largos. Cuando hay tres factores, se dice "tres", no "varios".
