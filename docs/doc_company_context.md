# Contexto de la empresa (para alimentar al copiloto)

STABLE context the AI copilot preloads before working on any spec. Fill this in once per
project, before running `/discovery` for the first time.

El contexto se divide por naturaleza del dato en tres documentos: este (estable, se
precarga), `docs/doc_market_research.md` (vivo, con fecha, cambia rápido, lo refresca la
skill `live-research`) y `docs/doc_open_questions.md` (lo que no sabemos, se pregunta al
equipo, nunca se inventa).

## Qué es la empresa

[COMPLETAR: quién es, a qué se dedica, en una o dos frases. Si esto no es una empresa
tradicional (un proyecto personal, un side project, un portfolio), decilo explícitamente
igual que acá.]

## Producto(s) core

[COMPLETAR: qué construye o vende, para quién. Si hay varios productos/líneas, listalos
con una frase cada uno.]

## Modelo de negocio

[COMPLETAR: cómo gana dinero hoy — o, si no aplica (proyecto sin monetización), decilo y
reformulá cuál es el "output" real que sí importa.]

## Cómo funciona el negocio (inferido vs. confirmado)

[COMPLETAR: hechos reales del negocio, cada uno tageado `[CONFIRMADO]` o
`[SUPUESTO — verificar]`. No mezcles los dos sin marcar cuál es cuál — esa es la regla
dura de este harness, ver `docs/doc_base_standards.md`.]

## Verticales / segmentos actuales

[COMPLETAR: a quién le vende o sirve hoy, con la mayor precisión posible — geografía,
tamaño de cliente, tipo de usuario.]

## Objetivos de negocio

[COMPLETAR: qué se está tratando de lograr, en orden de prioridad real (primario/
secundario/terciario), y cualquier restricción dura que las decisiones de producto no
puedan violar.]
