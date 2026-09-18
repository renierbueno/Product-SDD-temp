---
name: establish-design-system
description: Usar cuando hay que fijar (o revisar deliberadamente) la identidad visual del producto — paleta con escala real y tokens semánticos, tipografía con escala real, espaciado sistemático, elevación si aplica, contraste validado, un motivo de layout distintivo — para una versión de ALTA fidelidad. No es prerrequisito de un prototipo de baja fidelidad (eso sigue siendo build-prototype en gris/neutro), ni una decisión de modelo de monetización (eso es design-monetization-model). Produce un sistema de diseño fijado, documentado, accesible por construcción, y con craft real (no una paleta plana de 5 colores) que el resto del harness reutiliza.
---

# Fijar el sistema de diseño

Objetivo: decidir UNA vez la identidad visual del producto, no redecidirla en cada prototipo de alta fidelidad.

## Cuándo usarla

- El proyecto necesita por primera vez una versión de ALTA fidelidad (con marca real, no gris/neutro) de algo — no solo validar un flujo.
- Alguien pide explorar "direcciones de diseño", paletas, tipografía, o dice que algo "no se siente diferenciado/único" — esa es la señal de que la conversación se salió de validar un flujo y entró en identidad. Párala y muévela aquí, no la sigas resolviendo dentro de `build-prototype`.
- Se revisa deliberadamente cuando el contexto de marca cambió de verdad (p. ej. una decisión de marca ya fijada en otro canal, como un banner de LinkedIn, que ahora tiene que quedar consistente aquí), o cuando el proyecto creció lo suficiente para que valga la pena repetir el chequeo de distinctividad del Paso 2 (ver abajo — es un chequeo repetible, no un filtro de una sola vez).

## Qué NO es esta skill

- **No es prerrequisito de todo prototipo.** Un prototipo de baja fidelidad (gris/neutro, valida flujo, alcance y estados de error/borde) no necesita esperar a esto — es exactamente lo que `build-prototype` ya hace por defecto. El orden estándar de la industria es investigación → flujo en baja fidelidad → *después* diseño visual/alta fidelidad, no al revés (verificado vía research 2026-09-17: Nielsen Norman Group y múltiples guías de proceso UX coinciden en que la fidelidad visual se aplica en la etapa de alta fidelidad, no antes — señal FUERTE, varias fuentes independientes convergen).
- No valida un flujo ni estados de error/borde — eso sigue siendo `build-prototype`, en cualquier fidelidad.
- No es una decisión de modelo de negocio — `design-monetization-model` decide CÓMO se monetiza un touchpoint, no cómo se ve.
- No se repite cada sesión como `live-research` — se fija una vez, y las revisiones son deliberadas, nunca el resultado de "vamos probando cosas" dentro de otra skill.
- No es un sistema de componentes completo (atomic design, librería de UI) — eso es alcance de ingeniería/diseño de producto a más largo plazo. Esta skill fija identidad (paleta, tipografía, espaciado, elevación, un motivo de layout), no construye una librería.

## Insumos (léelos antes de proponer nada)

- `docs/doc_company_context.md` — quién es el operador, para quién es el producto, qué tono/voz ya existe en otros materiales reales (CV, voice guide, perfiles públicos).
- Cualquier decisión de marca YA fijada en otro canal (una paleta elegida para un banner, un logo, un producto hermano). Esta skill no inventa desde cero si ya hay una señal real de marca en otro sitio — la hereda y la razona, no la contradice sin decir por qué.

## Proceso

**Paso 1 — Encuentra la señal real, no la plantilla.** Busca en los insumos un detalle específico del sujeto (su propia voz, un valor personal, una decisión de marca ya tomada en otro canal) que ninguna propuesta genérica tendría. Una paleta o tipografía "porque se ve bien" no pasa este paso; tiene que explicarse desde el sujeto.

**Paso 2 — Evita el default de IA (chequeo repetible, no de una sola vez).** Antes de proponer, compara conscientemente contra los clichés conocidos (crema cálido + serif + acento terracota; casi-negro + un solo acento neón; Inter/Space Grotesk como tipografía "segura"; todo en tarjetas con esquinas redondeadas). Si la propuesta cae en uno, cámbiala y anota qué cambiaste y por qué. Este chequeo se repite cada vez que se revisa el sistema (no solo la primera vez) — un sistema que era distintivo hace seis meses puede volverse genérico si toda la categoría lo adoptó mientras tanto.

**Paso 3 — Construye la paleta como escala real, no colores sueltos.** Práctica estándar de la industria (verificado 2026-09-17, *Refactoring UI*, señal FUERTE): una paleta real tiene 8-10 tonos de gris y 5-10 variaciones por color clave, no 5 tokens planos. Primero los **primitivos** (valores hex crudos, nombre de familia + escala — ej. `graphite-800`), después los **semánticos** (cada primitivo mapeado a un rol de uso — ej. `color-bg-default -> graphite-800`). Al aclarar u oscurecer, rota el matiz (hacia amarillo/cian/magenta al aclarar, hacia rojo/verde/azul al oscurecer) en vez de solo mezclar blanco/negro — así no se lava el color. Cerca de los extremos (muy claro o muy oscuro), sube la saturación en vez de dejarla caer, o se ve deslavado.

**Paso 4 — Define una escala tipográfica real, no "2-3 tamaños que se ven bien".** Elige a mano una escala completa (ej. 12/14/16/18/20/24/30/36/48/64px), no unidades `em` que se puedan desalinear. Longitud de línea 45-75 caracteres. El line-height escala AL REVÉS que el tamaño: suelto para texto pequeño, apretado para titulares grandes.

**Paso 5 — Define una escala de espaciado no lineal.** Valores tipo 4/8/12/16/24/32/48/64px (~25% de salto entre valores adyacentes), no números arbitrarios. Más espacio ALREDEDOR de un grupo que DENTRO de él — así se percibe qué pertenece junto, sin necesitar un borde.

**Paso 6 — Sistema de elevación, solo si el diseño usa profundidad (tarjetas, modales, dropdowns).** 3-5 escalones reales (ej. botón < dropdown < modal), cada uno con su propio blur/offset — nunca la misma sombra reutilizada en todo. Si el layout no usa profundidad, se marca N/A explícitamente, no se omite en silencio.

**Paso 7 — Valida el contraste ANTES de fijar, no después, por prototipo.** Para cada par texto/fondo que el sistema realmente va a usar, calcula y documenta el ratio de contraste real (mínimo 4.5:1 texto normal, 3:1 texto grande y foco). Verificado 2026-09-17 (señal FUERTE, práctica estándar de la industria): la accesibilidad se valida en la capa de tokens, no se deja para que cada prototipo lo descubra por su cuenta.

**Paso 8 — Fija, no acumules opciones indefinidamente.** Presenta 2-3 direcciones reales (no diez variaciones de la misma), deja que el operador elija o mezcle, y CIERRA: la salida es un sistema fijado, no una lista abierta de posibilidades.

## Salida esperada

```
Paleta — primitivos: [escala completa por familia de color, no 5 tokens sueltos]
Paleta — semánticos: [cada primitivo mapeado a un rol de uso]
Escala tipográfica: [la escala completa hand-picked, con line-height por tamaño]
Escala de espaciado: [la escala no lineal completa]
Elevación/sombras: [3-5 escalones reales, o N/A explícito si el layout no usa profundidad]
Pares validados (contraste): [cada combinación texto/fondo real del sistema, con su ratio calculado]
Tipografía — familias: [2-3 con su rol — display / body / utilidad — y por qué esta combinación]
Motivo de layout distintivo: [1-2 frases — el mecanismo concreto que hace que esto no sea una plantilla genérica]
Toques finales considerados: [ej. bordes de acento, menos bordes generales, estados vacíos intencionales — opcional, solo lo que de verdad se va a usar]
Estilo de imagen/iconos: [opcional — solo si el proyecto realmente los usa]
Por qué encaja con el sujeto: [la señal real del Paso 1, explícita]
Qué NO hicimos a propósito: [el cliché evitado del Paso 2]
Estado: [FIJADO — con fecha — o EN PAUSA / EXPLORADO SIN CERRAR, nunca lo dejes ambiguo]
```

Guarda el resultado completo en `docs/doc_design_system.md`. Si el estado es EN PAUSA, dilo explícitamente — nunca dejes que el doc lea como fijado cuando no lo está.

## Cómo se conecta con el resto

Recibe contexto de `doc_company_context.md` y de cualquier decisión de marca ya fijada fuera del harness. Un `build-prototype` de ALTA fidelidad posterior lee `docs/doc_design_system.md` en vez de decidir color/tipografía de nuevo — y como el contraste ya viene validado por par, ese prototipo no tiene que re-chequear accesibilidad de color, solo usar los pares documentados. Un `build-prototype` de BAJA fidelidad no depende de esta skill en absoluto — puede correr antes, en paralelo, o sin que esta skill exista todavía.

## No está completo si...

- No está completo si la paleta o la tipografía no tienen una razón ligada al sujeto real, solo "se ve bien".
- No está completo si no se comparó conscientemente contra los clichés de diseño generado por IA conocidos.
- No está completo si los tokens de paleta son solo valores crudos sin capa semántica.
- No está completo si la paleta es una lista plana de 5 colores en vez de una escala real por familia.
- No está completo si no hay una escala tipográfica hand-picked, o una escala de espaciado no lineal.
- No está completo si el diseño usa profundidad (tarjetas, modales) y no hay un sistema de elevación real, o si no se marcó N/A explícitamente cuando no aplica.
- No está completo si algún par texto/fondo que el sistema realmente usa no tiene su ratio de contraste documentado.
- No está completo si queda como una lista abierta de opciones sin una decisión cerrada (o sin marcar EN PAUSA explícitamente).
- No está completo si el resultado no se guardó en `docs/doc_design_system.md`.
