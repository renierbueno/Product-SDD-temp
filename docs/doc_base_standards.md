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

## Cómo se cambia el harness

Aplica a cualquier edición de `CLAUDE.md`, `README.md`, `ai-specs/skills/*/SKILL.md`, `ai-specs/.commands/*.md`, o `docs/`, sin importar qué copiloto o sesión la haga.

- **Verifica integración antes de tocar nada.** Antes de editar una skill, un comando, o un doc, busca (grep) cada lugar donde el concepto que vas a cambiar ya se menciona — la tabla de rutas de `CLAUDE.md`, el diagrama de `README.md`, otros `SKILL.md`. Un cambio que rompe una referencia en otro archivo no está terminado, está a medias.
- **Toda skill/comando nuevo se declara en tres sitios, no en uno.** El archivo mismo (`ai-specs/skills/<nombre>/SKILL.md` + `ai-specs/.commands/<nombre>.md`), la tabla de rutas de `CLAUDE.md`, y el diagrama de estructura de `README.md`. Falta cualquiera de los tres y la skill existe pero es invisible para la próxima sesión.
- **Prueba antes y después, no solo después.** Antes de cambiar: comprueba qué es cierto hoy (cuenta cuántas skills/docs hay de verdad, qué referencias cruzadas existen). Después: repite la misma comprobación y verifica que coincide — ningún conteo ("cuatro docs", "once skills") puede quedar desincronizado con la realidad del repo.
- **Nada se asume, se comprueba.** Si la duda es sobre una práctica externa (¿cuál es el orden estándar de X?), eso es `live-research`, no una suposición razonada — igual que con cualquier otro dato de mercado.
- **Definición de "hecho" para un cambio al harness:** un copiloto en una sesión nueva, sin memoria de esta, tiene que poder seguir el rastro completo desde `CLAUDE.md` hasta el archivo final sin un solo enlace roto.

## Tono de escritura

Simple, directo, humano. Sin buzzwords, sin lenguaje que suene a IA. Sin guiones largos. Cuando hay tres factores, se dice "tres", no "varios".
