---
name: build-prototype
description: Usar para generar un prototipo funcional (HTML/React de un solo archivo) que muestra un flujo en vez de describirlo. Sirve para validar UX y alcance antes de comprometer ingeniería, y para mostrar algo tangible en vez de describirlo en una reunión. Lee los docs de contexto que aplican antes de inventar nada, identifica el momento pico y el cierre antes de construir, y se revisa contra un piso de usabilidad y accesibilidad real, no solo "funciona".
---

# Construir un prototipo con IA

Objetivo: mostrar el flujo, no contarlo. Un prototipo que no funciona de verdad pero deja ver las decisiones de UX y de alcance que tomaste, hecho por ti en minutos — y que se siente como el producto de verdad, no como una maqueta genérica.

## Cuándo usarla

- Te piden un feature de producto y quieres enseñar cómo se vería.
- Necesitas validar un flujo con un usuario sin esperar a ingeniería.
- Quieres alinear a Comercial o Dirección sobre el alcance antes de comprometer ingeniería.

**Esto valida UN flujo, no es el diseño final de todo el producto.** Un prototipo — aunque sea de alta fidelidad — es una herramienta de validación rápida y desechable, no el inventario completo y definitivo de cada pantalla/estado real (verificado 2026-09-17, señal MEDIA-FUERTE: incluso dentro de un mismo rol de diseño, "mockup de alta fidelidad" y "prototipo" son entregables distintos). Cuando ya se validó el flujo y toca producir el diseño completo de todas las pantallas reales para pasar a ingeniería, eso es `finalize-product-design` (`/finalize-design`), no más prototipos uno por uno.

**Fidelidad, por defecto BAJA.** Sin que te lo pidan explícitamente, este prototipo es de baja fidelidad: gris/neutro en paleta y tipografía, pero con contenido real y voz real (ver Insumos abajo) — "baja fidelidad" nunca significa contenido genérico, solo significa sin identidad visual. No esperes a que exista un sistema de diseño — el orden estándar de la industria es al revés (investigación → flujo en baja fidelidad → diseño visual en alta fidelidad, verificado 2026-09-17, NN/g y guías de proceso UX, señal FUERTE). Solo pasa a ALTA fidelidad si te lo piden explícitamente, y en ese caso lee `docs/doc_design_system.md` primero — si no existe, dilo y sugiere `establish-design-system` (`/design-system`) antes de inventar una paleta.

No la uses para decidir o iterar la identidad visual en sí (paleta, tipografía, look-and-feel) en NINGUNA fidelidad — eso es siempre `establish-design-system` (`/design-system`). Si la conversación empieza a girar en torno a si algo "se siente diferenciado" o a probar paletas, para y muévela ahí. La distinción visual (siempre neutra en baja fidelidad) es la única cosa que la fidelidad afecta — el contenido, la voz, y los mecanismos estructurales que ya se validaron NO se degradan solo por ser baja fidelidad.

## Insumos (lee esto antes de inventar nada)

Antes de construir, lee los docs de contexto que aplican — cada uno alimenta algo distinto, y cada uno evita un tipo de invención:

- **`docs/doc_company_context.md`** — quién es el usuario/operador real, qué hechos reales existen ya (contenido, cifras, casos). Úsalo en vez de inventar quién es la audiencia o qué dice el producto.
- **`docs/doc_market_research.md`** — cómo se comporta de verdad esta audiencia en este tipo de contexto (velocidad de lectura, canal de llegada, atención esperada). Úsalo para decidir qué tan rápido tiene que "aterrizar" el prototipo, no lo asumas.
- **`docs/doc_open_questions.md`** — qué NO está confirmado todavía. Si el prototipo necesita una respuesta que vive aquí, no la inventes: dilo explícitamente en el prototipo o en tu respuesta ("esto asume X, sin confirmar — ver doc_open_questions.md").
- **`docs/doc_design_system.md`** — identidad visual fijada, solo si el prototipo es de alta fidelidad (ver arriba).
- **`docs/doc_voice.md`** — voz y copy fijados, si existe. Úsalo tal cual para cualquier headline/copy que ya esté fijado ahí; no lo reescribas. Si el copy que hace falta no está fijado todavía, dilo y sugiere `lock-content-voice` (`/voice`) en vez de escribir copy nuevo al vuelo — mismo trato que el sistema de diseño con color.

**Regla de contenido: real primero, inventado solo si falta.** Todo dato, cifra o texto que ya existe en estos docs (o en el content-bank/fuente de verdad del proyecto) se usa tal cual — nunca genérico, nunca placeholder. Solo se inventa lo que genuinamente no está cubierto, y en ese caso se marca como tal (mismo criterio [CONFIRMADO]/[SUPUESTO] que el resto del harness), nunca se presenta como si fuera un hecho real. Esto no es solo higiene de datos — contenido real (no lorem ipsum, no copy genérico) es lo que hace que un prototipo dé retroalimentación útil en vez de una reacción vacía a texto de relleno.

## El momento pico y el cierre (antes de construir)

Antes de dibujar nada, identifica dos momentos concretos del flujo — no los trates como una lista plana de pantallas igual de importantes:

- **El pico**: el momento del flujo que más va a pesar en cómo alguien recuerda y juzga la experiencia completa (la prueba más fuerte, el resultado más sorprendente, el paso donde el valor real se hace obvio).
- **El cierre**: la última pantalla o acción antes de que la persona decida seguir o irse.

Diséñalos con más cuidado que el resto — la Peak-End Rule (Yablonski, *Laws of UX*) dice que la gente juzga una experiencia por su pico y su final, no por el promedio de todos los pasos. Un prototipo que trata sus cinco pantallas como igual de importantes está dejando esto sobre la mesa. Dilo explícitamente en tu respuesta: "el pico de este flujo es X, el cierre es Y" — no lo dejes implícito.

## Cómo pedirlo al copiloto

Dale contexto en este orden:

```
Construye un artifact [HTML / React de un solo archivo] que muestre:
- Pantalla: [ej. el terminal de pago pidiendo email tras una compra]
- El pico y el cierre de este flujo: [cuáles son, antes de construir]
- Estados a mostrar: [feliz, error, borde]
- Datos: [reales de los docs de contexto primero; lo inventado, marcado como tal]
- Restricción: sin backend, todo en estado local, sin librerías de storage del navegador
- Marca: por defecto colores neutros (baja fidelidad). Si es alta fidelidad, lee `docs/doc_design_system.md` y úsalo tal cual, no lo reinventes; si ese doc no existe todavía, dilo y sugiere `/design-system` en vez de improvisar uno.
```

## Qué mostrar, según el problema

- **Captación post-transacción**: pantalla tras completar una acción con un campo de contacto + un gancho de valor (cashback, garantía, contenido). Muestra el trade-off: fricción vs. captación.
- **Dashboard de campaña/operación**: vista de backoffice donde alguien crea o gestiona algo (formato, objetivo, presupuesto, reporte). Muestra el ciclo de vida completo.
- **Feature de vertical nueva**: la pantalla clave del flujo del usuario en ese vertical.

## Las leyes de UX que aplican siempre (Yablonski, *Laws of UX*)

No es una lista para citar, es para aplicar en cada decisión de layout/contenido:

- **Ley de Jakob**: la gente espera que lo nuevo funcione como lo que ya conoce. Navegación, formularios, patrones básicos → convencionales. Gasta el presupuesto de "diferente" solo en lo que de verdad es el diferenciador, no en reinventar un menú.
- **Ley de Hick**: más opciones = decisión más lenta. Menos ítems de navegación, un CTA claro, no varios compitiendo.
- **Regla del pico y el final (Peak-End)**: ver la sección de arriba — se identifica ANTES de construir, no después.
- **Efecto estético-usabilidad**: una interfaz que se ve mejor se percibe como más usable, y la primera impresión se forma en milisegundos y rara vez cambia después (ver `doc_market_research.md` si el proyecto tiene una cifra real de esto para su audiencia). Esto es la razón funcional, no solo estética, de por qué la fidelidad alta importa cuando toca usarla — no es vanidad visual.

## Checklist de usabilidad (Nielsen, antes de dar por terminado)

Repásalo contra el prototipo, no solo contra el camino feliz:

1. Visibilidad del estado del sistema — ¿se nota qué está pasando en cada momento?
2. Coincidencia con el mundo real — ¿el lenguaje y los conceptos son los que la audiencia ya usa?
3. Control y libertad del usuario — ¿hay una salida clara de cualquier acción no deseada?
4. Consistencia y estándares — ¿una misma acción se comporta igual en todo el prototipo?
5. Prevención de errores — ¿se puede evitar el error antes de que pase, no solo mostrarlo después?
6. Reconocer en vez de recordar — ¿la información necesaria está visible, o hay que memorizarla?
7. Flexibilidad y eficiencia — ¿funciona igual de bien para alguien que lo ve por primera vez y para alguien que vuelve?
8. Diseño estético y minimalista — ¿hay algo en pantalla que no sirve al objetivo principal?
9. Ayudar a reconocer, diagnosticar y recuperarse de errores — ¿el mensaje de error dice qué pasó y qué hacer, en lenguaje plano?
10. Ayuda y documentación — si hace falta explicar algo, ¿está donde se necesita, no escondido?

## Piso de accesibilidad (no negociable, en cualquier fidelidad)

- HTML semántico real (`<button>`, `<a>`, `<label>` con su `for`) en vez de `<div>`/`<span>` con estilo de botón — la accesibilidad nativa del navegador no se reconstruye a mano si no hace falta.
- Contraste de texto mínimo 4.5:1 (3:1 para texto grande) — se cumple aunque sea baja fidelidad en gris.
- Todo funcional por teclado: Tab/Shift+Tab navega, Enter/Espacio activa, Escape cierra overlays. Nunca un foco atrapado.
- Estado de foco visible siempre (mínimo 3:1 de contraste entre foco y no-foco) — nunca `outline: none` sin un reemplazo real.

## Reglas

- Un solo archivo, sin dependencias externas pesadas.
- Nada de localStorage/sessionStorage (no funciona en artifacts): usa estado en memoria.
- Contenido real primero (ver Insumos); lo inventado, marcado como tal — nunca lorem ipsum, nunca copy genérico de relleno.
- Que se vea el estado de error y el de borde, no solo el camino feliz. Ahí es donde se esconden los problemas reales de alcance.

## Por qué prototipar antes de pedírselo a ingeniería

Prototipar esto antes de pedírselo a ingeniería descarta problemas obvios de UX o de alcance. Así el PM no es el cuello de botella, e ingeniería recibe algo ya validado.

## Salida esperada

Un artifact que abre y deja navegar el flujo, con el pico y el cierre nombrados explícitamente en tu respuesta, no solo construidos.

## Cómo se conecta con el resto

Se usa junto a `write-spec`, no lo reemplaza: el spec (en su primera pasada, borrador) origina el prototipo; el prototipo es la validación de UX y alcance antes de pasarlo a ingeniería. Reordenado 2026-09-17: corre justo después del spec-borrador, ANTES de `validate-fast`/`human-validation` y antes de `establish-design-system`/`lock-content-voice` — el prototipo de baja fidelidad es la validación barata que decide si vale la pena invertir en las siguientes. En baja fidelidad no depende de `establish-design-system` en absoluto. En alta fidelidad (una vez el flujo ya se validó), lee el resultado de `establish-design-system` (`docs/doc_design_system.md`) — si esa skill no ha corrido todavía, esa es la anterior a invocar, no una variante de esta. Una vez el flujo está validado y, si aplica, la identidad/voz están fijadas, `finalize-product-design` es el siguiente paso para el inventario completo — no sigas corriendo más prototipos de alta fidelidad como sustituto de eso.

## No está completo si...

- No está completo si solo se muestra el camino feliz, sin estado de error ni de borde.
- No está completo si no va acompañado del spec que lo originó.
- No está completo si usa localStorage/sessionStorage o depende de un backend real.
- No está completo si tuvo que iterar sobre paleta/tipografía/identidad visual más de una vez dentro de esta skill, en cualquier fidelidad — esa es la señal de que la conversación se movió a trabajo de `establish-design-system` y debería continuar ahí, no aquí.
- No está completo si no leyó los docs de contexto que aplican antes de inventar datos, o si presentó contenido inventado como si fuera un hecho real sin marcarlo.
- No está completo si no nombró explícitamente el momento pico y el cierre del flujo antes de construir.
- No está completo si viola alguno de los 10 puntos del checklist de Nielsen o del piso de accesibilidad — ambos son parte de "terminado", no un extra opcional.
