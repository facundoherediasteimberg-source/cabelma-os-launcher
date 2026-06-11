# Onboarding manual — para Gemini CLI y Codex

Seguí este proceso si no tenés Claude Code.

---

## Opción 1 — Gemini CLI (gratis)

### Instalación

1. Instalá Node.js si no lo tenés: [nodejs.org](https://nodejs.org)
2. Instalá Gemini CLI:
   ```
   npm install -g @google/gemini-cli
   ```
3. Autenticá con tu cuenta Google:
   ```
   gemini auth
   ```

### Onboarding

1. Abrí una terminal en la carpeta del repo
2. Ejecutá `gemini`
3. Pegá este prompt:

```
Leé el archivo GEMINI.md y el archivo .claude/skills/cabelma-onboard/SKILL.md.
Ejecutá el proceso de onboarding que describe el skill:
haceme las preguntas una a la vez, esperá mis respuestas,
y al terminar generá los archivos que indica.
Empezá con la bienvenida del Paso 1.
```

---

## Opción 2 — Codex CLI (pago, OpenAI)

### Instalación

```
npm install -g @openai/codex
```

### Onboarding

1. Abrí una terminal en la carpeta del repo
2. Ejecutá `codex`
3. Pegá este prompt:

```
Leé el archivo AGENTS.md y el archivo .claude/skills/cabelma-onboard/SKILL.md.
Ejecutá el proceso de onboarding que describe el skill:
haceme las preguntas una a la vez, esperá mis respuestas,
y al terminar generá los archivos que indica.
Empezá con la bienvenida del Paso 1.
```

---

## Verificación

- [ ] `context/about-me.md` — tiene tu nombre y puesto
- [ ] `references/voice.md` — tiene tus muestras de escritura
- [ ] `context/schedule.md` — lista tus informes
- [ ] `connections.md` — lista tus herramientas
- [ ] `GEMINI.md` o `AGENTS.md` — tiene tu nombre (sin `{{placeholders}}`)
- [ ] `cabelma-intake.md` — registro de tus respuestas

---

## Cómo usar el AI después del onboarding

**Gemini CLI:**
```
gemini "en qué debería enfocarme esta semana"
```

**Codex:**
```
codex "en qué debería enfocarme esta semana"
```

---

## Comandos equivalentes a los skills

| En Claude Code | Manual |
|---|---|
| `/cabelma-onboard` | Seguí este archivo |
| `/cabelma-audit` | Pedile al AI: "Leé `.claude/skills/cabelma-audit/SKILL.md` y ejecutá el audit" |
| `/cabelma-level-up` | Pedile al AI: "Leé `.claude/skills/cabelma-level-up/SKILL.md` y corré la sesión" |
