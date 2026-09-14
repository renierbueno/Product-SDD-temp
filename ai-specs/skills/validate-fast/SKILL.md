---
name: validate-fast
description: Usar para definir la prueba más barata que confirma o mata una hipótesis antes de comprometer a ingeniería. Evita que el PM sea el cuello de botella pidiendo builds para validar cosas que se pueden validar sin código.
---

# Validar rápido, antes de escalar

Objetivo: no pedirle a ingeniería que construya algo para descubrir si la idea sirve. Definir la validación más barata primero.

## Paso 1 — Formula la hipótesis como algo falsable

```
Creemos que [usuario] hará [comportamiento] porque [razón].
Sabremos que es cierto si [métrica] supera [umbral] en [plazo].
Lo mataremos si [señal de fracaso].
```

## Paso 2 — Elige el método más barato que la responda

Ordena de más barato a más caro; usa el primero que responda de verdad:

1. **Datos que ya existen** — ¿Space ya tiene datos de otro vertical que respondan esto sin construir nada?
2. **Prueba de humo / fake door** — un botón o pantalla que mide intención sin backend real detrás.
3. **Concierge / manual** — resolver el flujo a mano para un operador antes de automatizarlo.
4. **Prototipo con IA** — un artifact que muestra el flujo para test con usuarios (enlaza `build-prototype`).
5. **MVP real** — solo si los cuatro anteriores no bastan.

## Paso 3 — Diseña el test concreto

```
Método elegido: [uno de los 5]
Con quién: [operador real / consumidor / equipo comercial]
Qué mide exactamente: [la métrica]
Umbral de éxito: [número]
Plazo: [días]
Coste (tiempo/dinero): [estimado]
```

Si el método elegido involucra hablar con personas reales (entrevista, concierge, prueba de humo con seguimiento), pasa a `human-validation` para el guion de ejecución: pedir compromiso en vez de opinión, tamaño de muestra, y cómo evitar que la cortesía se disfrace de validación.

## Regla de oro

Si la validación exige más esfuerzo de ingeniería que construir la feature entera, estás validando mal. Baja un escalón en la lista de métodos.

## Con datasets pequeños

Presenta el resultado como indicador direccional, no como conclusión. "Señal de que X" en vez de "queda demostrado que X".

## Salida esperada

La hipótesis falsable + el método elegido con su umbral. Tres líneas. Esto va dentro del spec, en la sección "cómo se valida".
