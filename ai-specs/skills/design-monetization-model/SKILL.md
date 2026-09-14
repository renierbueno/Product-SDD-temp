---
name: design-monetization-model
description: Usar cuando la pregunta es cómo monetizar un punto de interacción física (una máquina, una pantalla en un taxi, un asiento de estadio) sin romper la experiencia. Es el corazón del reto de retail media. Produce un modelo de monetización elegido entre varios posibles, con el trade-off razonado, no una regla ciega.
---

# Diseñar el modelo de monetización de un touchpoint

Objetivo: dado un punto de interacción física, elegir la forma de monetizarlo que mejor equilibra tres cosas en tensión. No hay una respuesta correcta fija; el trabajo es razonar el trade-off para ESTE punto y este contexto. Eso es exactamente lo que hace difícil el problema: escoger el mejor modelo para el negocio sin añadir fricción.

## El problema es de tres caras, siempre

Todo modelo de monetización de un touchpoint tiene que resolver a la vez:

1. **El dueño de la máquina/punto**: ¿por qué diría que sí? Rebaja de cuota, comisión por venta, un servicio nuevo que le da valor, datos de sus compradores. Sin su sí, nada corre.
2. **La marca / proveedor que paga**: ¿qué compra y por qué vale su dinero? Alcance, contexto, intención de compra en el momento.
3. **El comprador final**: su experiencia. Un proceso de venta casi automático se rompe fácil. Aquí vive la fricción.

## Paso 1 — Mapea los modelos posibles (no te cases con ads)

Advertising es uno, no el único. Para el touchpoint dado, lista cuáles aplican:

| Modelo | Qué es | Quién paga | Momento |
|---|---|---|---|
| Display / ad | Anuncio en pantalla | Marca | Antes / durante / después de la venta |
| Comisión por venta | La empresa se lleva % de una venta cruzada | Marca/proveedor | En la venta |
| Rebaja de cuota al operador | El operador cede espacio a cambio de pagar menos | (La empresa lo compensa con ingreso de marca) | Contrato |
| Reserva / pre-pedido | Comprar algo para recoger después | Comprador | Durante tiempo muerto |
| Ticketing / acceso | El punto es entrada a un evento/servicio | Comprador / organizador | Al acceder |
| Sesión pagada | Consulta/servicio online desde el punto | Comprador | En el punto |

## Paso 2 — El eje que lo decide todo: fricción vs. momento

Coloca cada modelo candidato según CUÁNDO toca al comprador:

- **Antes de la venta**: máxima fricción. Interrumpe a alguien que vino a comprar otra cosa. Casi siempre malo salvo que el contexto sea de espera larga.
- **Durante la venta**: rompe un proceso casi automático. Peligroso.
- **Después de la venta**: el reto es retener a alguien que ya se va. Necesita un gancho fuerte (cashback, pre-pedido útil) y segundos, no minutos.
- **En tiempo muerto**: la ventana de oro. Lavandería esperando, estadio antes del partido. Aquí caben reserva, pre-pedido, servicios.

## Paso 3 — El contexto físico manda

El mismo modelo gana o pierde según dónde esté el punto. Razónalo explícito:

```
Contexto: [aeropuerto / lavandería / taxi / estadio / oficina...]
Estado del comprador: [prisa / espera / cautivo / de paso]
Qué permite este contexto: [qué modelos tienen sentido aquí]
Qué NO permite: [qué rompería la experiencia aquí]
```

Ejemplo de razonamiento: en un aeropuerto la gente tiene prisa, un ad antes de la venta es fricción pura; pero un pre-pedido "recoge en la puerta de embarque" usa la prisa a favor. En un estadio el comprador está cautivo y con tiempo muerto: pre-pedir comida desde el asiento y recogerla a la salida es alto valor y cero fricción en el momento de consumo.

## Paso 4 — Elige y razona el trade-off (sin jerarquía fija)

No hay un eje que siempre gana. Sopesa los tres y declara tu decisión:

```
Modelo elegido: [uno]
Qué gana el operador: [su incentivo para aceptar]
Qué gana la marca/proveedor: [por qué paga]
Fricción para el comprador: [dónde toca y por qué es aceptable AQUÍ]
Por qué este y no los otros dos candidatos: [el trade-off explícito]
Qué lo mataría: [la condición que lo hace inviable]
```

La frase clave para decir en voz alta: "no elijo el modelo que más ingresa, ni el que menos molesta, en abstracto; elijo el que mejor equilibra los tres para este punto y este contexto, y digo qué estoy sacrificando."

## Nota plataforma vs. específico

El contexto físico se modela como una variable configurable (tipo de ubicación, estado del comprador, ventana de tiempo), no como un build por sitio. Un buen modelo de monetización es una capacidad que se parametriza por contexto. Eso lo mantiene fiel al mandato de no crear un mosaico inmantenible.

## Salida esperada

El mapa de modelos posibles + la decisión razonada del paso 4. Encadena con `write-spec` para la capacidad elegida y con `validate-fast` para la prueba de dos caras (ver nota abajo).

## Validación de dos caras

Un modelo de touchpoint no se valida con una sola métrica. Necesitas señal de los dos lados: ¿el operador acepta el trato? ¿la marca paga? ¿el comprador no abandona? La prueba más barata suele ser probar primero el lado más frágil (normalmente la aceptación del operador o la fricción del comprador), no el que es más fácil de medir.
