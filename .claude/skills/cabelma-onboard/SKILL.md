# /cabelma-onboard

Configura el Cabelma-OS de un nuevo usuario en una sola sesión.
Hace 9 preguntas y genera los archivos de configuración con las respuestas.
Compatible con Claude Code, Gemini CLI y Codex.

**Cuándo correr:** primera vez que abrís el repo. También si cambiás de rol o querés actualizar tu perfil.

---

## Paso 1 — Bienvenida

Mostrá este mensaje exacto:

```
Bienvenido/a a Cabelma-OS.

Voy a hacerte 9 preguntas para configurar tu asistente AI personal.
No necesitás saber nada de tecnología. Solo contestar con honestidad.

Cuando terminemos, tu AI va a saber:
- Quién sos y qué hacés en Cabelma
- Cómo hablás
- Qué informes y tareas manejás
- Con qué herramientas trabajás

Después de esto, podés preguntarme cualquier cosa relacionada con tu trabajo.

¿Empezamos? Escribí "sí" para arrancar.
```

Esperá confirmación antes de continuar.

---

## Paso 2 — Las 9 preguntas

Hacé una pregunta a la vez. Esperá la respuesta antes de pasar a la siguiente.

### Q1 — Nombre y puesto

```
1/9 — ¿Cuál es tu nombre completo y cuál es tu puesto en Cabelma?
Ejemplo: "Juan García, analista de producción"
```

Guardá: `nombre`, `puesto`.

### Q2 — Área

```
2/9 — ¿A qué área pertenecés?
  A) Producción  B) Supply Chain  C) Comercial  D) Administración
  E) Control de Gestión  F) RRHH  G) IT  H) Dirección  I) Otra
```

Guardá: `area`.

### Q3 — A quién reportás

```
3/9 — ¿A quién le mandás información regularmente?
Decime nombre, puesto y qué tipo de info les mandás.
```

Guardá: `stakeholders`.

### Q4 — Voz

```
4/9 — Pegá 1-2 cosas que hayas escrito en el trabajo recientemente.
Puede ser un mensaje de WhatsApp, un mail, cualquier cosa. Sin editar.
```

**Regla:** si el usuario dice que no tiene nada, pedile que busque en WhatsApp o Outlook. No avanzar sin al menos una muestra.

Guardá: `voz_samples` (verbatim).

### Q5 — Informes y entregables

```
5/9 — ¿Qué informes o entregables generás regularmente?
Para cada uno: nombre, frecuencia, a quién va.
```

Guardá: `informes`.

### Q6 — Herramientas

```
6/9 — ¿Con qué herramientas y sistemas trabajás día a día?
Ejemplo: Excel, Softland, Power BI, Python, PAD, Teams, etc.
```

Si mencionan **Softland**: activar `usa_softland = true`.
Guardá: `herramientas`.

### Q7 — Dolor principal

```
7/9 — ¿Cuál es la tarea que más tiempo te lleva cada semana y que más te gustaría simplificar?
```

Guardá: `dolor_principal`.

### Q8 — Módulos Softland (condicional)

Solo si `usa_softland = true`:

```
8/9 — ¿A qué módulos de Softland tenés acceso?
  CO-Compras  FC-Finanzas  ST-Stock  SC-Producción  BI-Reportes  VT-Ventas
```

Si no usa Softland, decir: `8/9 — Salteo esta pregunta (no mencionaste Softland).`

Guardá: `modulos_softland`.

### Q9 — Reglas del área

```
9/9 — ¿Hay algo de tu área que el AI deba conocer?
- Cómo se hacen ciertas cosas
- Excepciones o casos raros
- Reglas que no están escritas pero todos saben

Si no se te ocurre nada, podés completar context/about-business.md después.
```

Guardá: `reglas_area`.

---

## Paso 3 — Scaffold de archivos

**Si ya existen archivos anteriores:** moverlos a `archives/onboard-YYYY-MM-DD/` antes de sobreescribir.

### context/about-me.md
```markdown
# Sobre mí
**Nombre:** {nombre} | **Puesto:** {puesto} | **Área:** {area}

## A quién le reporto
{lista de stakeholders}

## Mi dolor principal
{dolor_principal}
```

### context/priorities.md
Inferí 2-3 prioridades de Q5 y Q7.
```markdown
# Prioridades — próximos 90 días
> Inferidas del onboarding. Editá según lo que vos considerés prioritario.
1. {de dolor_principal}
2. {del informe más importante}
3. Mejorar el uso del AI en el trabajo diario
```

### references/voice.md
```markdown
# Mi registro de voz
## Muestras (verbatim)
{voz_samples — sin modificar}
## Instrucción
Cuando redactes por mí, igualá formalidad, longitud de oraciones y vocabulario de las muestras.
```

### context/schedule.md
Tabla con los informes de Q5.

### connections.md
Tabla con las herramientas de Q6. Si usa Softland, incluir fila con módulos.

### context/about-business.md
```markdown
# Reglas de negocio — {area}
## Lo que me contaste en el onboarding
{reglas_area}
## Para agregar más
Editá este archivo cuando encuentres algo que el AI debería saber.
```

### CLAUDE.md, AGENTS.md y GEMINI.md
Reemplazar `{{nombre}}`, `{{puesto}}`, `{{area}}` con los valores reales en los tres archivos.

### cabelma-intake.md
Registro con todas las respuestas y la fecha.

---

## Paso 4 — Cierre

```
✓ Listo. Tu Cabelma-OS está configurado.

Ahora sé quién sos, qué hacés, cómo hablás y con qué trabajás.

Para arrancar: preguntame "¿en qué debería enfocarme esta semana?"
En 7 días: corré /cabelma-audit para ver qué tan bien está tu setup.
```
