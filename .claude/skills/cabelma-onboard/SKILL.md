# /cabelma-onboard

Configura el Cabelma-OS de un nuevo usuario en una sola sesión.
Entrevista de 9 preguntas + scaffold de archivos al final.
Idempotente: se puede volver a correr en cualquier momento.

**Cuándo correr:** primera vez que abrís el repo. También si cambiás de rol o querés actualizar tu perfil.

---

## Paso 1 — Leer el intake existente

Leer `cabelma-intake.md`. Verificar qué secciones Q1-Q9 tienen contenido vs. `[Tu respuesta aquí]`.

- **Todo completo** → saltar al Paso 3 (scaffold).
- **Parcialmente completo** → preguntarle al usuario: "Veo que Q1, Q3, Q4 ya tienen respuesta. ¿Completamos el resto ahora o scaffoldeamos con lo que hay?" Su decisión.
- **Vacío (primer run)** → ejecutar Paso 2.

---

## Paso 2 — La entrevista (9 preguntas, tope fijo)

Una pregunta a la vez. Escribir cada respuesta en `cabelma-intake.md` a medida que llegan (para poder retomar si se interrumpe).

Si una respuesta está demasiado vaga, pedir más detalle una sola vez antes de pasar a la siguiente.

---

### Q1 — Identidad + cliente interno

```
1/9 — ¿Cuál es tu nombre completo, tu puesto y tu área?
¿A quién le entregás información o resultados — quién depende de lo que producís?

Ejemplo: "Facundo García, analista de producción en el área de Producción.
Le entrego el informe diario de fallas a Fabián (supervisor) y el reporte mensual a Daniela (Control de Gestión)."
```

Guardar internamente: `nombre`, `puesto`, `area`, `stakeholders`.

---

### Q2 — Voz

```
2/9 — Pegá 1-2 cosas que hayas escrito vos en el trabajo recientemente.
No las edites antes de pegar.

Puede ser un mensaje de WhatsApp, un mail, un comentario en Teams, lo que sea.
Lo importante: que sea tuyo y que lo pegues tal cual.
```

**Regla dura — no negociable.** Si el usuario empieza a escribir texto nuevo en lugar de pegar algo real, responder exactamente esto:

> *"Pará — pegalo tal cual. Si lo escribís acá mientras hablamos, la muestra ya está influida por esta conversación. Abrí tu último mail o historial de WhatsApp en otra ventana y pegá el texto sin editar. Es la única regla que no puedo doblar."*

Pedir dos muestras. Dos mails, dos mensajes, o una de cada. No avanzar hasta tener al menos una muestra real.

Guardar internamente: `voz_samples` (texto verbatim, sin modificar).

---

### Q3 — Prioridades 90 días

```
3/9 — ¿Cuáles son tus 2-3 prioridades más importantes para los próximos 90 días?

No "mejorar los procesos" — necesito algo concreto: un número, una fecha, un entregable específico.

Ejemplo: "Automatizar el informe de producción semanal para el 31 de agosto.
Reducir el tiempo de cierre mensual de 3 días a 1 día."
```

**Push-back obligatorio** si la respuesta es vaga (ej: "mejorar mis reportes", "trabajar mejor con el AI"):

> *"Eso es un objetivo, no una prioridad ejecutable. ¿Qué informe específico? ¿Para cuándo? ¿Cuánto tiempo te lleva ahora y cuánto debería llevarte?"*

Guardar internamente: `prioridades`.

---

### Q4 — Sistemas y datos

```
4/9 — ¿Con qué sistemas y herramientas trabajás día a día?
¿Dónde vive la información que usás y producís?

Ejemplo: "Excel, Softland, Power BI. Los datos vienen de Softland,
los informes los armo en Excel y los mando por mail."
```

Si mencionan **Softland**: activar bandera interna `usa_softland = true`.

Guardar internamente: `herramientas`, `donde_viven_datos`.

---

### Q5 — Comunicación

```
5/9 — ¿Cómo te comunicás con las personas que usan lo que hacés?
¿Email, Teams, WhatsApp, reuniones, otro?

¿Y con tu equipo directo?
```

Guardar internamente: `canales_comunicacion`.

---

### Q6 — Informes y entregables

```
6/9 — ¿Qué informes o entregables generás regularmente?

Para cada uno, decime:
- Nombre del informe
- Frecuencia (diario, semanal, mensual, etc.)
- A quién va
```

Guardar internamente: `informes` (lista de objetos {nombre, frecuencia, destinatario}).

---

### Q7 — Dolor principal

```
7/9 — ¿Cuál es la tarea que más tiempo te lleva cada semana y que más te gustaría simplificar?

No tiene que ser tecnológico. Puede ser cualquier cosa: armar un Excel, copiar datos,
esperar que alguien te mande algo, revisar lo mismo todos los días.
```

Guardar internamente: `dolor_principal`.

---

### Q8 — Módulos de Softland (condicional)

Solo si `usa_softland = true`:

```
8/9 — ¿A qué módulos de Softland tenés acceso?

  CO — Compras
  FC — Finanzas / Contabilidad
  ST — Stock / Almacenes
  SC — Producción (Supply Chain)
  BI — Reportes / Business Intelligence
  VT — Ventas
  Otro (decime cuál)
```

Si `usa_softland = false`, saltar y avisar:

```
8/9 — Salteo esta porque no mencionaste Softland.
```

Guardar internamente: `modulos_softland`.

---

### Q9 — Reglas del área

```
9/9 — Última. ¿Hay algo de tu área o tu trabajo que sea importante que el AI conozca?

Puede ser:
- Cómo se hacen ciertas cosas en tu sector
- Excepciones o casos raros que siempre aparecen
- Reglas que no están escritas pero todos saben
- Cosas que cambian seguido

Si no se te ocurre nada ahora, podés editarlo después en context/about-business.md.
```

Guardar internamente: `reglas_area`.

---

## Paso 3 — Scaffold (un solo batch)

Con todas las respuestas, generar los archivos en una sola pasada. No confirmar archivo por archivo.

**Si ya existen archivos de un run anterior**, moverlos a `archives/onboard-YYYY-MM-DD-HHMM/` antes de sobreescribir.

---

### 3.1 — `context/about-me.md`

```markdown
# Sobre mí

**Nombre:** {nombre}
**Puesto:** {puesto}
**Área:** {area}

## A quién le entrego resultados

{para cada stakeholder: "- {nombre} ({puesto si lo mencionó}): {tipo de info que le manda}"}

## Mi dolor principal

{dolor_principal}
```

---

### 3.2 — `context/priorities.md`

Con las prioridades de Q3 exactamente como las dijo el usuario. No parafrasear.

```markdown
# Prioridades — próximos 90 días

1. {prioridad 1 verbatim}
2. {prioridad 2 verbatim}
3. {prioridad 3 si la hay}

## Cuándo revisar esto

Al inicio de cada mes o cuando cambien los objetivos.
```

---

### 3.3 — `references/voice.md`

```markdown
# Mi registro de voz

## Muestras (verbatim)

{voz_samples — pegar exactamente como las escribió el usuario, sin modificar una sola palabra}

## Cómo usar estas muestras

Cuando redactes por mí, igualá:
- El nivel de formalidad
- La longitud de las oraciones
- Los signos de puntuación y mayúsculas que uso
- El vocabulario técnico o coloquial

No añadas frases de cortesía ni cierres formales si no aparecen en las muestras.
No imites mi voz en contenido externo sin mostrarme un borrador primero.
```

---

### 3.4 — `context/schedule.md`

```markdown
# Calendario de informes y entregables

| Informe / Entregable | Frecuencia | Destinatario | Notas |
|---|---|---|---|
{para cada informe: "| {nombre} | {frecuencia} | {destinatario} | |"}
```

---

### 3.5 — `connections.md`

```markdown
# Sistemas y herramientas

| # | Sistema / Herramienta | Uso | Mecanismo AI | Auth | Última revisión |
|---|---|---|---|---|---|
{para cada herramienta: "| {n} | {herramienta} | {uso inferido de Q4+Q5+Q6} | no conectado | — | — |"}

## Notas de conexión

- Para conectar una herramienta con el AI, editá la columna "Mecanismo AI": script / MCP / API / manual
- Las auth keys y paths van en `.env` (nunca en este archivo)
```

Si `usa_softland = true`, agregar fila:
`| Softland ERP | {modulos_softland separados por coma} | UI automation / script | no conectado | — | — |`

---

### 3.6 — `context/about-business.md`

```markdown
# Reglas de negocio — {area}

> Lo que el AI no puede saber por sí solo. Solo vos sabés esto.

## Lo que me contaste en el onboarding

{reglas_area — texto libre del usuario, sin modificar}

## Para agregar más

Editá este archivo directamente cuando encuentres algo que el AI no sepa y debería saber.
```

---

### 3.7 — `CLAUDE.md`, `AGENTS.md` y `GEMINI.md`

Reemplazar todos los `{{placeholders}}` en los tres archivos:
- `{{nombre}}` → nombre
- `{{puesto}}` → puesto
- `{{area}}` → area

---

### 3.8 — `cabelma-intake.md`

```markdown
# Cabelma-OS Intake — {nombre}

**Fecha:** {fecha de hoy}
**Área:** {area}

## Respuestas

**Q1 — Identidad y cliente interno:** {respuesta}
**Q2 — Muestras de voz:** {respuesta}
**Q3 — Prioridades 90 días:** {respuesta}
**Q4 — Sistemas y datos:** {respuesta}
**Q5 — Comunicación:** {respuesta}
**Q6 — Informes:** {respuesta}
**Q7 — Dolor principal:** {respuesta}
**Q8 — Módulos Softland:** {respuesta o "N/A"}
**Q9 — Reglas del área:** {respuesta}
```

---

## Paso 4 — Pantalla de cierre

Tres líneas. No más.

```
✓ Listo. Tu Cabelma-OS sabe quién sos, qué hacés, cómo hablás y qué querés lograr este trimestre.

Hoy: preguntame — "¿en qué debería enfocarme esta semana?"
Día 7: corré /cabelma-audit para ver cómo está tu setup.
```

**Cuando el usuario haga la pregunta de cierre** ("¿en qué debería enfocarme esta semana?"), responder usando solo los archivos de contexto recién generados:
- Lista de 3 bullets, en el registro de voz de Q2
- Cada bullet conectado a una prioridad de Q3
- Línea final: *"Si tuviera que elegir una sola cosa para el lunes, sería [X], porque [razón de las prioridades]. ¿Querés que arranquemos con eso? — y pregunta palanca: ¿hasta dónde podría llegar el AI acá?"*

La pregunta palanca siembra el Marco CAI antes de que `/cabelma-level-up` lo formalice.

---

## Reglas de implementación críticas

1. **Tope de 9 preguntas.** No agregar Q10 en conversación.
2. **Voz: la regla del paste es no negociable.** Si el usuario escribe texto nuevo en lugar de pegar, rechazar y pedir el paste real.
3. **Scaffold en una sola pasada.** Después de Q9, generar todos los archivos de una. Sin confirmación archivo por archivo.
4. **Idempotente.** Re-correr con intake editado refresca los archivos de contexto y hace backup de los anteriores. Saltear preguntas ya respondidas salvo que el usuario quiera revisarlas.
5. **Pantalla de cierre: tres líneas.** No un menú.
6. **No generar skills nuevas.** El kit viene con 3; el usuario las amplía con `/cabelma-level-up`.
7. **No escribir en `.env`.** Las credenciales son Día 2, no Día 1.
8. **Escribir en cabelma-intake.md a medida que llegan las respuestas** (no al final), para poder retomar si se interrumpe.

---

## Verificación (para el implementador)

- **Test frío:** clonar repo limpio, correr onboarding, completar 9 respuestas, verificar que se generan los 8 archivos, hacer la pregunta de cierre y confirmar que cita Q2 + Q3 + Q7 específicamente. Genérico = falla.
- **Idempotencia:** re-correr con una prioridad de Q3 cambiada. Esperado: solo `context/priorities.md` y `CLAUDE.md` se actualizan; backup creado en `archives/onboard-{ts}/`.
- **Rechazo de voz:** escribir una muestra en medio de la conversación. Esperado: el skill rechaza y pide el paste real.
