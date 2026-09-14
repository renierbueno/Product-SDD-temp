---
name: build-prototype
description: Usar para generar un prototipo funcional (HTML/React de un solo archivo) que muestra un flujo en vez de describirlo. Sirve para validar UX y alcance antes de comprometer ingeniería, y para mostrar algo tangible en la prueba en vivo.
---

# Construir un prototipo con IA

Objetivo: mostrar el flujo, no contarlo. Un prototipo que no funciona de verdad pero deja ver las decisiones de UX y de alcance que tomaste, hecho por ti en minutos.

## Cuándo usarla

- La prueba pide un feature de producto y quieres enseñar cómo se vería.
- Necesitas validar un flujo con un usuario sin esperar a ingeniería.
- Quieres demostrar en vivo que prototipas tú mismo (esto es lo que le llamó la atención al director).

## Cómo pedirlo al copiloto

Dale contexto en este orden:

```
Construye un artifact [HTML / React de un solo archivo] que muestre:
- Pantalla: [ej. el Spot pidiendo email tras un pago con tarjeta]
- Estados a mostrar: [feliz, error, borde]
- Datos de ejemplo: [inventa datos plausibles del vertical]
- Restricción: sin backend, todo en estado local, sin librerías de storage del navegador
- Marca: colores neutros, se personaliza con la del operador
```

## Qué mostrar, según el problema

- **Acquisition on the spot**: pantalla del Spot post-pago con un QR o campo de email + el gancho de cashback. Muestra el trade-off: fricción vs. captación.
- **Dashboard de campaña (retail media)**: vista de Space donde un operador crea una campaña para una marca (formato, PDVs objetivo, presupuesto, reporte). Muestra el ciclo de vida de la campaña.
- **Feature de vertical nueva**: la pantalla clave del flujo del operador o del consumidor en ese vertical.

## Reglas

- Un solo archivo, sin dependencias externas pesadas.
- Nada de localStorage/sessionStorage (no funciona en artifacts): usa estado en memoria.
- Datos de ejemplo plausibles, no lorem ipsum.
- Que se vea el estado de error y el de borde, no solo el camino feliz. Eso demuestra que piensas como PM, no como diseñador.

## Frase para decir mientras lo generas

"Antes de pedirle esto a ingeniería lo prototipo yo para descartar problemas obvios de UX o de alcance. Así no soy el cuello de botella y ellos reciben algo ya validado."

## Salida esperada

Un artifact que abre y deja navegar el flujo. Acompáñalo del spec (skill write-spec) para que quede claro que el prototipo es la validación, no el entregable final.
