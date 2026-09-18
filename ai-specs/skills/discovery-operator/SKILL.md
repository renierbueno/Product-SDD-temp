---
name: discovery-operator
description: Usar al inicio de un problema abierto, cuando hay que entender qué hace un negocio, un vertical o un touchpoint antes de proponer nada. Es el paso cero del proceso. Produce el mapa del problema real, no una lista de features pedidas.
---

# Discovery de operador

Objetivo: entender el negocio y el contexto real lo bastante para separar el problema real del problema aparente. Nadie te va a dar el problema bien planteado; tu trabajo es encontrarlo.

## Cuándo usarla

- El problema llega abierto ("entiende qué hacemos y trae una propuesta").
- Te dan un vertical o un touchpoint nuevo y no sabes por dónde entrar.
- Alguien te pide una feature concreta y sospechas que no es el problema de fondo.

## Las preguntas, en tres capas

No preguntes features. Pregunta por el negocio, el flujo y el contexto, en este orden:

**Capa 1 — El negocio**
- ¿Cómo gana dinero hoy? ¿Cuál es su margen?
- ¿Qué le quita el sueño: captar clientes, entregar el servicio, mantener la operación, cobrar?
- ¿Quién es el cliente final y qué sabe de él hoy? (normalmente: menos de lo que cree)

**Capa 2 — El flujo real**
- Recorre conmigo una interacción de principio a fin: ¿qué pasa antes, durante y después del momento central?
- ¿Dónde se cae la gente? ¿Dónde pierde dinero el negocio?
- ¿Cuánto dura la interacción? ¿Hay prisa o tiempo muerto? (esto define qué se puede hacer en ese punto)

**Capa 3 — El contexto**
- ¿Dónde y cómo ocurre esto? (un contexto con prisa no es lo mismo que uno con espera, ni uno con multitud lo mismo que uno individual)
- ¿Qué cambia el contexto sobre lo que el cliente aceptaría o ignoraría?

## Separar dolor real de capricho

Para cada cosa que te cuenten, pregúntate:
- ¿Esto lo dijeron porque les duele, o porque se lo imaginan bonito?
- ¿Hay evidencia de que ya intentaron resolverlo? (dolor real = ya intentaron algo)
- ¿Cuánto les cuesta hoy no resolverlo? Si no lo saben, probablemente no es prioritario.

Marca cada hallazgo: [DOLOR CONFIRMADO] / [SUPUESTO — validar] / [DESEO sin evidencia].

## Salida esperada

```
Negocio: [quién es, cómo gana dinero]
Flujo real: [antes → momento central → después, con el punto de dolor marcado]
Contexto y qué implica: [dónde/cómo ocurre, prisa/tiempo, qué permite]
Problema real (una frase): [el de fondo, no el que te pidieron]
Lo que sé vs. lo que asumo: [lista corta, cada uno tagueado]
```

Una frase de problema bien encontrada vale más que diez features.

## Cómo se conecta con el resto

Si sales de discovery con el problema real y el contexto entendido, sigue con `design-monetization-model` (si el problema es de monetización de un touchpoint) o `evaluate-vertical` (si el problema es si entrar o no en un vertical).

## No está completo si...

- No está completo si no se separó negocio, flujo y contexto en las tres capas.
- No está completo si algún hallazgo no quedó tagueado (DOLOR CONFIRMADO / SUPUESTO — validar / DESEO sin evidencia).
- No está completo si el "problema real" resulta ser la misma feature que te pidieron al principio.
