---
name: discovery-operator
description: Usar al inicio de un problema abierto, cuando hay que entender qué hace un operador, un vertical o un touchpoint antes de proponer nada. Es el paso cero del rol. Produce el mapa del problema real, no una lista de features pedidas.
---

# Discovery de operador

Objetivo: entender el negocio del operador y el contexto del punto de servicio lo bastante para separar el problema real del problema aparente. Nadie te va a dar el problema bien planteado; tu trabajo es encontrarlo.

## Cuándo usarla

- La prueba empieza abierta ("entiende qué hacemos y trae una propuesta").
- Te dan un vertical o un touchpoint nuevo y no sabes por dónde entrar.
- Alguien te pide una feature concreta y sospechas que no es el problema de fondo.

## Las preguntas, en tres capas

No preguntes features. Pregunta por el negocio, el flujo y el dolor, en este orden:

**Capa 1 — El negocio del operador**
- ¿Cómo gana dinero hoy con estas máquinas/puntos? ¿Cuál es su margen?
- ¿Qué le quita el sueño: captar ubicaciones, llenar máquinas, reponer, averías, cobrar?
- ¿Quién es el comprador final y qué sabe de él hoy? (normalmente: casi nada)

**Capa 2 — El flujo real**
- Recorre conmigo una venta de principio a fin: ¿qué pasa antes, durante y después del pago?
- ¿Dónde se cae la gente? ¿Dónde pierde dinero el operador?
- ¿Cuánto dura la interacción? ¿El comprador tiene prisa o tiempo muerto? (esto define qué se puede hacer en ese punto)

**Capa 3 — El contexto físico**
- ¿Dónde están las máquinas? (aeropuerto con prisa ≠ lavandería con espera ≠ estadio con multitud)
- ¿Qué cambia el contexto sobre lo que el comprador aceptaría o ignoraría?

## Separar dolor real de capricho

Para cada cosa que te cuenten, pregúntate:
- ¿Esto lo dijeron porque les duele, o porque se lo imaginan bonito?
- ¿Hay evidencia de que ya intentaron resolverlo? (dolor real = ya intentaron algo)
- ¿Cuánto les cuesta hoy no resolverlo? Si no lo saben, probablemente no es prioritario.

Marca cada hallazgo: [DOLOR CONFIRMADO] / [SUPUESTO — validar] / [DESEO sin evidencia].

## Salida esperada

```
Operador: [quién es, cómo gana dinero]
Flujo de venta: [antes → pago → después, con el punto de dolor marcado]
Contexto físico y qué implica: [dónde está, prisa/tiempo, qué permite]
Problema real (una frase): [el de fondo, no el que te pidieron]
Lo que sé vs. lo que asumo: [lista corta, cada uno tagueado]
```

Una frase de problema bien encontrada vale más que diez features. Si sales de discovery con eso y el contexto físico entendido, encadena con `design-monetization-model` o `evaluate-vertical`.
