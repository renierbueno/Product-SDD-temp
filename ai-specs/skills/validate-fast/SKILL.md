---
name: validate-fast
description: Usar para definir la prueba más barata que confirma o mata una hipótesis antes de comprometer a ingeniería. Evita que el PM sea el cuello de botella pidiendo builds para validar cosas que se pueden validar sin código.
---

# Validar rápido, antes de escalar

Objetivo: no pedirle a ingeniería que construya algo para descubrir si la idea sirve. Definir la validación más barata primero.

## Cuándo usarla

- Hay una hipótesis de producto y hace falta la prueba más barata que la confirme o la mate.
- Alguien está a punto de pedirle un build a ingeniería para algo que se podría validar sin código.
- Toca rellenar la sección "cómo se valida" de un spec.

## Paso 1 — Formula la hipótesis como algo falsable

```
Creemos que [usuario] hará [comportamiento] porque [razón].
Sabremos que es cierto si [métrica] supera [umbral] en [plazo].
Lo mataremos si [señal de fracaso].
```

## Paso 2 — Elige el método más barato que la responda

Ordena de más barato a más caro; usa el primero que responda de verdad:

1. **Datos que ya existen** — ¿el backoffice/analítica ya tiene datos de otro contexto que respondan esto sin construir nada?
2. **Prueba de humo / fake door** — un botón o pantalla que mide intención sin backend real detrás.
3. **Concierge / manual** — resolver el flujo a mano antes de automatizarlo.
4. **Prototipo con IA** — un artifact que muestra el flujo para test con usuarios (enlaza `build-prototype`).
5. **MVP real** — solo si los cuatro anteriores no bastan.

## Paso 3 — Diseña el test concreto

```
Método elegido: [uno de los 5]
Con quién: [socio operativo real / usuario final / equipo comercial]
Qué mide exactamente: [la métrica]
Umbral de éxito: [número]
Plazo: [días]
Coste (tiempo/dinero): [estimado]
```

## Regla de oro

Si la validación exige más esfuerzo de ingeniería que construir la feature entera, estás validando mal. Baja un escalón en la lista de métodos.

## Con datasets pequeños

Presenta el resultado como indicador direccional, no como conclusión. "Señal de que X" en vez de "queda demostrado que X".

## Salida esperada

La hipótesis falsable + el método elegido con su umbral. Tres líneas. Esto va dentro del spec, en la sección "cómo se valida".

## Cómo se conecta con el resto

Recibe de `write-spec` (la sección "cómo se valida", escrita en su primera pasada) y de `build-prototype` (reordenado 2026-09-17: corre justo después del prototipo de baja fidelidad, así que valida contra el flujo real que ya existe, no solo contra una hipótesis en papel). Si el método elegido involucra hablar con personas reales (entrevista, concierge, prueba de humo con seguimiento), sigue con `human-validation` para el guion de ejecución.

## No está completo si...

- No está completo si la hipótesis no es falsable, es decir, no dice qué la mataría.
- No está completo si se eligió un método sin antes descartar los más baratos de la lista.
- No está completo si falta el umbral numérico de éxito.
