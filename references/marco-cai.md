# Marco CAI — Cabeza · Acción · Infraestructura

El Marco CAI es la forma de pensar sobre automatización en Cabelma.
Tiene tres capas. Cada capa responde una pregunta distinta.

---

## Capa 1 — Cabeza
*¿Cómo pensar antes de automatizar?*

**Pregunta Palanca**
Ante cualquier tarea nueva: "¿qué parte de esto podría hacer el AI?"
No "¿puedo usar AI acá?" — sí "¿qué parte?" (obliga a descomponer).

**Descomposición**
Toda tarea es: obtener datos → procesar → presentar → distribuir.
Identificá en cuál de esos pasos está el mayor costo y empezá ahí.

**Regla de los 10 minutos**
Si probar si el AI puede hacer algo lleva menos de 10 minutos, probalo primero.

---

## Capa 2 — Acción
*¿Cómo decidir qué automatizar?*

**Encontrá la restricción real**
"Si esto se resolviera mágicamente mañana, ¿qué seguiría siendo lento?" — eso es lo que vale atacar.

**Mapeá el proceso completo**
Antes de automatizar un paso, entendé el flujo entero. Automatizar en el medio de un proceso manual suele crear más fricción.

**Escala de autonomía**
1. AI asiste — te da opciones, vos decidís
2. AI propone — redacta/calcula, vos revisás
3. AI ejecuta con revisión — lo hace pero te avisa
4. AI ejecuta solo — sin intervención

Empezá en nivel 1 o 2. Subí solo cuando confíes en el resultado.

**Criterio de resultado**
Si no podés decir "esto mejora [X] en [Y]", la idea no está definida.

---

## Capa 3 — Infraestructura
*¿Cómo construirlo y mantenerlo?*

**Principio Lego** — una función por pieza. Si algo falla, que falle en un lugar identificable.

**Línea de ensamblaje** — cada paso valida antes de pasar al siguiente.

**Regla del Becario** — escribí las instrucciones como si se las explicaras a alguien que llegó hoy. Si dejás algo implícito, el AI lo va a asumir mal.

**Método Bici** — usalo al 80% y corregí sobre la marcha. Mejor que esperar la versión perfecta.

**Freno de Emergencia** — toda automatización tiene un punto de stop manual. Siempre sabés cómo frenarla.

---

## Cómo usar este marco

- No sabés por dónde empezar → **Cabeza**: aplicá Pregunta Palanca.
- Muchas ideas, no sabés cuál elegir → **Acción**: aplicá Criterio de resultado.
- Idea clara pero ejecución trabada → **Infraestructura**: aplicá Principio Lego.

Cuando corrés `/cabelma-level-up`, este marco guía la conversación.
