---
name: design-monetization-model
description: Usar cuando la pregunta es cómo monetizar un punto de contacto compartido (una pantalla, un espacio, una interacción) sin romper la experiencia de quien lo usa. Produce un modelo de monetización elegido entre varios posibles, con el trade-off razonado, no una regla ciega.
---

# Diseñar el modelo de monetización de un touchpoint

Objetivo: dado un punto de contacto compartido entre varias partes, elegir la forma de monetizarlo que mejor equilibra tres cosas en tensión. No hay una respuesta correcta fija; el trabajo es razonar el trade-off para ESTE punto y este contexto. Eso es exactamente lo que hace difícil el problema: escoger el mejor modelo para el negocio sin añadir fricción.

## Cuándo usarla

- Te preguntan cómo monetizar un punto de contacto concreto (una pantalla, un espacio, un momento de la experiencia de alguien).
- Ya se decidió entrar en un vertical o touchpoint y toca elegir el modelo de ingreso.
- Alguien propone "pongamos ads" y hace falta comparar esa opción con las demás antes de aceptarla.

## El problema es de tres caras, siempre

Todo modelo de monetización de un touchpoint compartido tiene que resolver a la vez:

1. **El dueño del punto**: ¿por qué diría que sí? Rebaja de cuota, comisión por venta, un servicio nuevo que le da valor, datos de sus usuarios. Sin su sí, nada corre.
2. **El tercero que paga**: ¿qué compra y por qué vale su dinero? Alcance, contexto, intención en el momento.
3. **El usuario final**: su experiencia. Un proceso casi automático se rompe fácil. Aquí vive la fricción.

## Paso 1 — Mapea los modelos posibles (no te cases con ads)

Advertising es uno, no el único. Para el touchpoint dado, lista cuáles aplican:

| Modelo | Qué es | Quién paga | Momento |
|---|---|---|---|
| Display / ad | Anuncio en el punto de contacto | Tercero | Antes / durante / después de la interacción |
| Comisión por venta | La empresa se lleva % de una venta cruzada | Tercero | En la venta |
| Rebaja de cuota al dueño del punto | Cede espacio a cambio de pagar menos | (Se compensa con ingreso del tercero) | Contrato |
| Reserva / pre-pedido | Comprar algo para recoger o usar después | Usuario final | Durante tiempo muerto |
| Ticketing / acceso | El punto es entrada a un evento/servicio | Usuario final / organizador | Al acceder |
| Sesión pagada | Consulta/servicio desde el punto | Usuario final | En el punto |

## Paso 2 — El eje que lo decide todo: fricción vs. momento

Coloca cada modelo candidato según CUÁNDO toca al usuario final:

- **Antes de la interacción**: máxima fricción. Interrumpe a alguien que vino a hacer otra cosa. Casi siempre malo salvo que el contexto sea de espera larga.
- **Durante la interacción**: rompe un proceso casi automático. Peligroso.
- **Después de la interacción**: el reto es retener a alguien que ya se va. Necesita un gancho fuerte (cashback, pre-pedido útil) y segundos, no minutos.
- **En tiempo muerto**: la ventana de oro — cualquier momento de espera real dentro del contexto. Aquí caben reserva, pre-pedido, servicios.

## Paso 3 — El contexto manda

El mismo modelo gana o pierde según dónde y cuándo ocurre el punto de contacto. Razónalo explícito:

```
Contexto: [describe el entorno real: con prisa, con espera, cautivo, de paso...]
Estado del usuario: [prisa / espera / cautivo / de paso]
Qué permite este contexto: [qué modelos tienen sentido aquí]
Qué NO permite: [qué rompería la experiencia aquí]
```

Ejemplo de razonamiento (genérico, adapta al contexto real): si el usuario tiene prisa, un ad antes de la interacción es fricción pura; pero un pre-pedido que resuelve algo útil más tarde usa la prisa a favor. Si el usuario está cautivo y con tiempo muerto real, ofrecer algo para usar al salir es alto valor y cero fricción en el momento central de la interacción.

## Paso 4 — Elige y razona el trade-off (sin jerarquía fija)

No hay un eje que siempre gana. Sopesa los tres y declara tu decisión:

```
Modelo elegido: [uno]
Qué gana el dueño del punto: [su incentivo para aceptar]
Qué gana el tercero que paga: [por qué paga]
Fricción para el usuario final: [dónde toca y por qué es aceptable AQUÍ]
Por qué este y no los otros dos candidatos: [el trade-off explícito]
Qué lo mataría: [la condición que lo hace inviable]
```

El criterio en una frase: no se elige el modelo que más ingresa, ni el que menos molesta, en abstracto; se elige el que mejor equilibra los tres para este punto y este contexto, dejando explícito qué se sacrifica.

## Nota plataforma vs. específico

El contexto se modela como una variable configurable (tipo de punto, estado del usuario, ventana de tiempo), no como un build por sitio. Un buen modelo de monetización es una capacidad que se parametriza por contexto. Eso lo mantiene fiel al principio de no crear un mosaico inmantenible.

## Validación de dos caras

Un modelo de touchpoint no se valida con una sola métrica. Necesitas señal de los dos lados: ¿el dueño del punto acepta el trato? ¿el tercero paga? ¿el usuario final no abandona? La prueba más barata suele ser probar primero el lado más frágil (normalmente la aceptación del dueño del punto o la fricción del usuario final), no el que es más fácil de medir.

## Salida esperada

El mapa de modelos posibles (paso 1) + la decisión razonada (paso 4): modelo elegido, qué gana cada una de las tres caras, y qué lo mataría.

## Cómo se conecta con el resto

Sigue con `write-spec` para la capacidad elegida, y con `validate-fast` para diseñar la prueba de dos caras de arriba.

## No está completo si...

- No está completo si no se nombraron los tres lados (dueño del punto, tercero que paga, usuario final) y qué gana cada uno.
- No está completo si no se dijo en qué momento (antes / durante / después de la interacción / tiempo muerto) toca al usuario el modelo elegido.
- No está completo si "advertising" fue el único modelo que se consideró.
- No está completo si no se dijo qué lo mataría.
