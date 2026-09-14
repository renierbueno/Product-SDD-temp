# product-sdd — Harness de Spec-Driven Development

Andamiaje portable para llevar una idea de producto de cero a validado sin ser el cuello de botella de ingeniería. Está pensado para usarse con Claude, Cursor o Codex indistintamente: hay una única fuente canónica en `ai-specs/` y cada copiloto lee de ahí.

La filosofía es la que se volvió estándar en 2026: el spec es el artefacto durable y ejecutable, el prompt es desechable. El PM es dueño del `specify` (problema, historia de usuario, criterios de aceptación, fuera de alcance); ingeniería es dueña del `plan` y las `tasks`. La entrega es limpia porque el spec está estructurado, no porque haya una conversación que alguien tenga que descifrar.

## Cómo se usa en una sesión (el flujo de 60 minutos)

El orden sigue el ciclo completo del PM. No toda prueba usa todas las skills; eliges según el problema:

1. **Descubrir** — si el problema es abierto, `skills/discovery-operator` te da el guion para entender el negocio, el flujo y el contexto físico, y encontrar el problema real.
2. **Elegir modelo** — si va de monetizar un touchpoint (retail media), `skills/design-monetization-model` te ayuda a elegir entre los modelos posibles sopesando operador, marca y fricción del comprador, sin jerarquía fija.
3. **Encuadrar vertical** — si es "¿deberíamos entrar en X?", `skills/evaluate-vertical` con la matriz plataforma-vs-específico.
4. **Argumentar** — `skills/business-case` para defender la decisión en términos de negocio y resolver build-vs-integrate.
5. **Priorizar** — si hay varias opciones, `skills/prioritize-roadmap` da el marco con criterio explícito.
6. **Especificar** — `skills/write-spec` produce el spec en formato EARS, el artefacto que entregas a ingeniería.
7. **Validar qué** — `skills/validate-fast` define la prueba más barata que confirma o mata la hipótesis.
8. **Validar cómo** — `skills/human-validation` es el guion de ejecución con personas reales: pedir compromiso en vez de opinión, tamaño de muestra, evitar señales falsas. Especialmente necesario en modelos de varias caras (operador, marca, comprador).
9. **Prototipar** — `skills/build-prototype` genera un artifact funcional para mostrar el flujo en vez de contarlo.

## Estructura

```
.
├── ai-specs/                       # fuente canónica; .claude/ .codex/ .cursor/ son symlinks hacia aquí
│   ├── .agents/        # roles que el copiloto puede adoptar
│   ├── .commands/      # utilidades ligeras
│   └── skills/         # los flujos reutilizables (entrypoint principal)
│       ├── discovery-operator/
│       ├── design-monetization-model/
│       ├── evaluate-vertical/
│       ├── business-case/
│       ├── prioritize-roadmap/
│       ├── write-spec/
│       ├── validate-fast/
│       ├── human-validation/
│       └── build-prototype/
├── docs/               # contexto de la empresa/producto — plantilla, se rellena por proyecto
└── README.md
```

## Por qué esto y no un PRD

Un PRD de treinta páginas escrito antes de un prototipo es papeleo waterfall, no SDD. Aquí escribes el mínimo spec que elimina la ambigüedad para la siguiente fase, y validas los supuestos temprano. Los criterios de aceptación van en formato condición-comportamiento (EARS) porque así mapean casi uno a uno con casos de prueba, que es exactamente lo que necesita un agente de IA o un ingeniero para no tener que adivinar qué quisiste decir.

## Cómo empezar en un proyecto nuevo

Rellena `docs/doc_company_context.md` con el contexto real de la empresa/producto antes de invocar la primera skill — todas lo leen como punto de partida.
