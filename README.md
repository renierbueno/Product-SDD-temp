# product-sdd — Harness de Spec-Driven Development

Andamiaje portable para llevar una idea de producto de cero a validado sin ser el cuello de botella de ingeniería. Está pensado para usarse con Claude, Cursor o Codex indistintamente: hay una única fuente canónica en `ai-specs/` y cada copiloto lee de ahí.

La filosofía es la que se volvió estándar en 2026: el spec es el artefacto durable y ejecutable, el prompt es desechable. El PM es dueño del `/spec` (problema, historia de usuario, criterios de aceptación, fuera de alcance); ingeniería es dueña del `/plan` y las `tasks`. La entrega es limpia porque el spec está estructurado, no porque haya una conversación que alguien tenga que descifrar.

## Cómo se usa en una sesión

Cada skill es un comando real (`.claude/commands/`, ver Estructura abajo), no solo texto para invocar por descripción. El orden sigue el ciclo completo del PM — **reordenado 2026-09-17** tras auditar cómo equipos de producto AI-native (Anthropic, OpenAI, Google, Meta) secuencian esto en la práctica real: el prototipo se mueve temprano, antes de comprometer validación formal o identidad visual, en vez de ser casi el último paso. No todo problema usa todas las skills; eliges según cuál sea:

1. **Descubrir** — `/discovery`, si el problema es abierto, te da el guion para entender el negocio, el flujo y el contexto físico, y encontrar el problema real.
2. **Elegir modelo** — `/monetize`, si va de monetizar un touchpoint compartido, te ayuda a elegir entre los modelos posibles sopesando el dueño del punto, el tercero que paga, y la fricción del usuario final, sin jerarquía fija.
3. **Encuadrar vertical** — `/evaluate`, si es "¿deberíamos entrar en X?", con la matriz plataforma-vs-específico.
4. **Argumentar** — `/business-case` para defender la decisión en términos de negocio y resolver build-vs-integrate.
5. **Priorizar** — `/prioritize`, si hay varias opciones, da el marco con criterio explícito.
6. **Especificar — borrador** — `/spec` produce un spec EARS ligero: la decisión ya tomada, convertida en algo que origina el prototipo y, si aplica, la hipótesis que `validate-fast` va a rellenar. No es la versión final — esa llega después de `finalize-product-design`, ver más abajo.
7. **Prototipar** — `/prototype` genera un artifact funcional para mostrar el flujo en vez de contarlo. Por defecto es de BAJA fidelidad (gris/neutro) — no necesita identidad visual fijada. Valida UN flujo rápido, antes de invertir en validación formal o en pulir la marca; no es el diseño final de todo el producto.
8. **Validar qué** — si aplica, `/validate` define la prueba más barata que confirma o mata la hipótesis — ahora contra el prototipo real que ya existe, no solo una hipótesis en papel.
9. **Validar cómo** — si aplica, `/human-validate` es el guion de ejecución con personas reales: pedir compromiso en vez de opinión, tamaño de muestra, evitar señales falsas. Especialmente necesario en modelos de varias caras (dueño del punto, tercero que paga, usuario final). En un proyecto solo/sin usuarios externos que validar, esto lo puede reemplazar una revisión directa del propio PM — sigue siendo un chequeo real, solo que informal, no una de las 13 skills.

`/design-system` no es un paso numerado del flujo lineal, y no es prerrequisito de todo prototipo — solo de uno de ALTA fidelidad (con marca real), y solo una vez que el flujo de baja fidelidad ya pasó por el paso 8/9 de arriba. Orden estándar verificado (2026-09-17, Nielsen Norman Group y guías de proceso UX): investigación → flujo en baja fidelidad → diseño visual en alta fidelidad, no al revés. Se invoca una vez por proyecto, cuando se necesita esa versión de alta fidelidad por primera vez, y no se repite cada sesión — solo se revisita con una revisión deliberada de marca. Si la conversación dentro de `/prototype` empieza a girar en torno a paleta, tipografía o "esto no se siente diferenciado", esa es la señal de volver a `/design-system` en vez de seguir iterando ahí.

`/voice` tampoco es un paso numerado — es el equivalente de `/design-system` pero para palabras (verificado 2026-09-17, práctica real de content design: la voz se fija con reglas Do/Don't accionables y ejemplos reales, nunca adjetivos sueltos, y el tono varía por contexto aunque la voz se mantenga constante). Sin esto, el copy se decide al vuelo dentro de `/prototype` — la misma deriva que ya pasó con color antes de que existiera `/design-system`. Se fija una vez, se revisa solo deliberadamente. Mismo momento que `/design-system`: después del flujo validado, antes de invertir en el inventario completo.

`/finalize-design` tampoco es un paso numerado del flujo lineal — viene DESPUÉS de `/prototype` (flujo validado) y `/design-system`/`/voice` (identidad y voz fijadas), cuando hace falta el diseño completo y definitivo de cada pantalla/estado real, listo para ingeniería. No es lo mismo que un prototipo de alta fidelidad: verificado (2026-09-17, señal MEDIA-FUERTE) que incluso dentro de un mismo rol de diseño, "mockup de alta fidelidad" (la referencia completa) y "prototipo" (la validación rápida de un flujo) son entregables distintos. Bundlearlos fue exactamente la confusión que esta skill separada evita.

**Especificar — versión final**, después de `/finalize-design`: se vuelve a invocar `write-spec` (misma skill, segunda pasada) para revisar y cerrar el spec con lo que realmente quedó validado y finalizado — no con lo que se esperaba al principio. Esto es lo que `/plan` toma como artefacto durable, junto con el inventario de `/finalize-design` cuando existe.

`/research` tampoco es un paso fijo del flujo, pero por la razón opuesta a `/design-system`: se invoca ad hoc cada vez que falta un dato de mercado en cualquiera de los pasos anteriores, y busca en el momento en vez de asumir. `/plan` no lo usa el PM: toma el spec ya finalizado y lo ejecuta el agente `engineer` — y cuando el proyecto necesitó `/finalize-design`, es ESE inventario completo el que `/plan` construye, no el prototipo de validación.

## Estructura

```
.
├── ai-specs/                       # fuente canónica; .claude/ .codex/ .cursor/ son symlinks hacia aquí
│   ├── .agents/        # roles que el copiloto puede adoptar
│   ├── .commands/      # comandos reales: /discovery /monetize /evaluate /business-case
│   │                   # /prioritize /spec /prototype /validate /human-validate
│   │                   # /design-system /voice /finalize-design /research /plan
│   └── skills/         # los flujos reutilizables, uno por comando (misma forma en las 13)
│       ├── discovery-operator/
│       ├── design-monetization-model/
│       ├── evaluate-vertical/
│       ├── business-case/
│       ├── prioritize-roadmap/
│       ├── write-spec/
│       ├── validate-fast/
│       ├── human-validation/
│       ├── establish-design-system/
│       ├── lock-content-voice/
│       ├── build-prototype/
│       ├── finalize-product-design/
│       └── live-research/
├── docs/               # doc_base_standards.md (cómo se decide/especifica/valida/cambia
│   │                     # el harness, se precarga siempre) + el contexto, partido en
│   │                     # cinco por naturaleza del dato:
│   ├── doc_base_standards.md      # estándares base del harness — genérico, ya viene completo
│   ├── doc_company_context.md     # estable, se precarga (qué es la empresa, producto, negocio) — plantilla, llenala antes de arrancar
│   ├── doc_market_research.md     # vivo, con fecha, lo refresca skills/live-research — plantilla
│   └── doc_open_questions.md      # lo que no sabemos, se pregunta al equipo, no se inventa — plantilla, arranca vacía
├── specs/               # salida real de /spec para este proyecto — empieza vacía
└── README.md
```

`docs/doc_design_system.md` y `docs/doc_voice.md` no vienen en el repo — no son plantillas para llenar a mano, son SALIDA de `establish-design-system` y `lock-content-voice` (se crean solas la primera vez que corrés esas skills). Si una skill que los necesita no los encuentra, te lo va a decir y te va a sugerir cuál correr antes — no hace falta crearlos vos.

El principio detrás del split de `docs/`: lo estable se precarga, lo que cambia rápido se busca en el momento, lo que no sabemos se pregunta (nunca se inventa), y una decisión de diseño se fija una vez y se reutiliza — no se vuelve a decidir en cada prototipo.

## Por qué esto y no un PRD

Un PRD de treinta páginas escrito antes de un prototipo es papeleo waterfall, no SDD. Aquí escribes el mínimo spec que elimina la ambigüedad para la siguiente fase, y validas los supuestos temprano. Los criterios de aceptación van en formato condición-comportamiento (EARS) porque así mapean casi uno a uno con casos de prueba, que es exactamente lo que necesita un agente de IA o un ingeniero para no tener que adivinar qué quisiste decir.

## Cómo empezar en un proyecto nuevo

1. Usá el botón **"Use this template"** de GitHub para crear tu propia copia (o cloná el repo directamente).
2. Rellená `docs/doc_company_context.md` con el contexto real de tu empresa/producto antes de invocar la primera skill — todas lo leen como punto de partida.
3. Corré `/discovery` (o el comando que aplique si ya tenés el problema claro — ver la tabla de arriba).

`docs/doc_market_research.md` y `docs/doc_open_questions.md` se van poblando durante el trabajo, no antes: el primero vía `skills/live-research`, el segundo a mano cuando surge una pregunta que solo el equipo puede responder. Este repo no trae ejemplos resueltos ni datos de ninguna empresa concreta — son específicos de cada proyecto; cada `SKILL.md` describe su propio formato de salida esperado.

## Uso real

Este es el harness que uso para construir mi propio trabajo — incluyendo mi portfolio profesional, que corrió el flujo completo (discovery → priorización → spec → prototipo → validación) antes de escribir una sola línea de código del sitio. No es un ejercicio teórico.

## Licencia

MIT — ver `LICENSE`. Usalo, adaptalo, quedátelo.
