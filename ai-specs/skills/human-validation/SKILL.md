---
name: human-validation
description: Usar una vez que validate-fast eligió el método (prueba de humo, concierge, entrevista). Esta skill es el CÓMO ejecutarlo bien: guion, tamaño de muestra, y cómo evitar que la cortesía de la gente se disfrace de validación. Especialmente importante en modelos de dos o tres caras (dueño del punto, tercero que paga, usuario final).
---

# Ejecutar la validación con humanos

Objetivo: que la validación mida comportamiento real, no opiniones educadas. El error más común no es elegir mal el método, es ejecutarlo de forma que todo el mundo te diga que sí.

## Cuándo usarla

- `validate-fast` ya eligió el método (prueba de humo, concierge, entrevista) y toca ejecutarlo bien.
- El modelo tiene dos o tres caras (dueño del punto, tercero que paga, usuario final) y hay que validar cada una por separado.
- Hay riesgo de que la cortesía de la gente se disfrace de validación.

## Regla de oro: pide compromiso, no opinión

"¿Te gustaría esto?" casi siempre da un sí falso, la gente es amable. Pregunta lo que le cuesta algo:

| En vez de preguntar | Pregunta / observa esto |
|---|---|
| "¿Pagarías por esto?" | "Aquí tienes el link de pago, complétalo si te interesa" |
| "¿Te molestaría un anuncio aquí?" | Muéstraselo de verdad y mide si abandona |
| "¿Usarías el pre-pedido?" | Ofrécelo una vez y mide si lo completa, no si dice que sí |
| "¿Aceptarías este trato?" | Pon la cifra concreta sobre la mesa (rebaja de X€ o comisión de Y%) y mide si firma o pide pensarlo |

La señal real está en la fricción que la persona está dispuesta a cruzar, no en la palabra que dice.

## Cuántas personas necesitas (y por qué no hace falta más)

Para una señal direccional temprana, no para un lanzamiento:

- **Usabilidad / fricción de un flujo**: 5 personas detectan la mayoría de los problemas obvios. Después de la quinta, empiezas a ver los mismos problemas repetidos.
- **Deseo o intención de compra**: 10 a 15 conversaciones dan una lectura direccional razonable. Menos de eso, cualquier patrón puede ser ruido.
- **Aceptación del socio operativo (B2B, decisión cara)**: 3 a 5 conversaciones reales bastan si son con el perfil correcto, porque cada conversación B2B pesa mucho más que una encuesta de consumidor.

Con muestras así de pequeñas, el resultado se reporta siempre como indicador direccional, nunca como conclusión.

## El guion, para cada cara del modelo

**Con el usuario final**
1. Deja que use el flujo sin ayudarlo. No expliques qué esperas que haga.
2. Cuando se atasque, no lo rescates de inmediato, anota dónde y por cuánto tiempo.
3. Al final, pregunta "cuéntame qué pasó por tu cabeza en el momento X" (retrospectiva de un momento concreto), no "¿qué te pareció?" (opinión general).
4. Nunca preguntes si algo "es buena idea". Pregunta si lo haría de nuevo, o si lo recomendaría a alguien concreto.

**Con el dueño del punto / socio operativo**
1. No le vendas la idea en la misma conversación en la que la validas, contamina la señal.
2. Pon la cifra real sobre la mesa (rebaja de cuota de X€, o comisión de Y%), no "estaríamos pensando en algo así".
3. Mide la reacción a la cifra, no a la idea en abstracto. Si duda con la cifra puesta, esa duda es el dato.
4. Cierra pidiendo un siguiente paso concreto (piloto real, firma de intención), no "¿qué opinas?".

**Con el tercero que pagaría**
1. Habla con alguien que ya compra algo comparable hoy, no con cualquier contacto genérico.
2. Pregunta qué pagan hoy por algo equivalente, para tener un ancla de precio real.
3. La señal fuerte es que pidan una propuesta formal o un piloto pagado, no que digan "interesante".

## Señales falsas que hay que descartar

- Todo el mundo dice que sí en la entrevista, pero nadie completó el compromiso pedido: la idea gusta en abstracto, no en la práctica. Señal débil.
- Solo validaste con gente que ya te cae bien o que conoces: sesgo de simpatía. Repite con desconocidos antes de confiar en el resultado.
- Preguntaste por el futuro ("¿lo usarías?") en vez de por el pasado o el presente ("¿lo usaste ahora?", "cuéntame la última vez que te pasó algo parecido"): la gente predice mal su propio comportamiento futuro.

## Cómo comunicarlo

La forma corta de explicar cómo se ejecuta esto, sin quedarse solo en listar métodos: "no le pregunto si le gusta, le pido que haga algo que le cueste un poco, y si lo hace, esa es la señal. Con datos tan chicos como los que tendría en una primera ronda, lo trato como indicador, no como conclusión."

## Salida esperada

```
Método ejecutado: [de validate-fast]
Con quién y cuántos: [perfil + número]
Compromiso pedido (no opinión): [qué le costó algo a la persona]
Lo que se observó: [comportamiento real, no lo que dijeron sentir]
Señal: [FUERTE / MIXTA / DÉBIL] — nunca "confirmado" con muestra chica
Lo que lo mataría si se repitiera: [el patrón negativo que invalidaría la idea]
```

## Cómo se conecta con el resto

Recibe de `validate-fast` una vez elegido el método. El resultado (señal FUERTE / MIXTA / DÉBIL) alimenta la decisión ya planteada en `business-case` o `design-monetization-model`.

## No está completo si...

- No está completo si alguna pregunta del guion pide opinión en vez de compromiso.
- No está completo si la muestra no llega al mínimo de esa categoría (5 para usabilidad, 10-15 para intención de compra, 3-5 para aceptación B2B).
- No está completo si la señal se reporta como "confirmado" con una muestra chica.
