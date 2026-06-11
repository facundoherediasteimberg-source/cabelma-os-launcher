# Cabelma-OS

Tu asistente AI personal para trabajar en Cabelma S.A.

---

## ¿Qué es esto?

Un sistema preconfigurado para que cualquier persona de Cabelma pueda tener su propio AI de trabajo.
No reemplaza tu criterio. Te ayuda a trabajar más rápido.

Después de configurarlo, el AI va a saber:
- Quién sos y qué hacés
- Qué informes y tareas manejás
- Cómo hablás
- Con qué herramientas trabajás

---

## Cómo empezar

Elegí el AI que más te convenga. Todos leen este repo y funcionan igual.

| AI | Costo | Cómo instalarlo | Archivo que usa |
|---|---|---|---|
| **Claude Code** | Pago (Claude Pro) | [claude.ai/code](https://claude.ai/code) | `CLAUDE.md` |
| **Gemini CLI** | Gratis | [g.co/gemini-cli](https://g.co/gemini-cli) | `GEMINI.md` |
| **Codex CLI** | Pago (OpenAI) | `npm install -g @openai/codex` | `AGENTS.md` |

### Opción A — Claude Code

1. Instalá Claude Code
2. Cloná este repo y abrilo en Claude Code
3. Escribí `/cabelma-onboard` y seguí las instrucciones

### Opción B — Gemini CLI (gratis)

1. Instalá Gemini CLI
2. Cloná este repo
3. Desde la carpeta del repo, ejecutá `gemini`
4. Pegá: `Leé GEMINI.md y .claude/skills/cabelma-onboard/SKILL.md y corré el onboarding`

### Opción C — Codex CLI

1. Instalá Codex: `npm install -g @openai/codex`
2. Cloná este repo
3. Desde la carpeta del repo, ejecutá `codex`
4. Seguí `MANUAL-ONBOARD.md`

---

## Estructura del repo

```
cabelma-os-launcher/
├── CLAUDE.md                  ← instrucciones del AI (Claude Code)
├── AGENTS.md                  ← instrucciones del AI (Codex)
├── GEMINI.md                  ← instrucciones del AI (Gemini CLI)
├── connections.md             ← tus sistemas conectados
├── cabelma-intake.md          ← registro de tu onboarding (se crea solo)
├── context/
│   ├── cabelma-general.md     ← info general de Cabelma (pre-cargado)
│   ├── about-me.md            ← sobre vos (se llena con /cabelma-onboard)
│   ├── about-business.md      ← reglas de tu área (ídem)
│   ├── schedule.md            ← tus informes y entregables (ídem)
│   ├── priorities.md          ← tus prioridades (ídem)
│   └── pending.md             ← pendientes
├── references/
│   ├── marco-cai.md           ← cómo pensar sobre automatización
│   └── voice.md               ← tu registro de escritura (se llena con /cabelma-onboard)
├── decisions/
│   └── log.md                 ← registro de decisiones
└── .claude/skills/
    ├── cabelma-onboard/       ← /cabelma-onboard
    ├── cabelma-audit/         ← /cabelma-audit
    └── cabelma-level-up/      ← /cabelma-level-up
```

---

## Skills disponibles

| Comando | Qué hace | Cuándo usarlo |
|---|---|---|
| `/cabelma-onboard` | Configura tu OS (9 preguntas) | Primera vez, o para actualizar tu perfil |
| `/cabelma-audit` | Evalúa qué tan bien funciona tu setup | Al final de la primera semana, luego mensualmente |
| `/cabelma-level-up` | Encontrá la próxima tarea a automatizar | Semanalmente |

---

## Preguntas frecuentes

**¿Tengo que saber programar?**
No. Solo necesitás tener Claude Code, Gemini CLI o Codex, y contestar 9 preguntas.

**¿Mis datos son privados?**
Todo queda en tu computadora. Este repo no sube datos personales a ningún servidor externo.
Las credenciales van en `.env`, que está en el `.gitignore` y nunca se sube a GitHub.

**¿Puedo compartir mi configuración con otro compañero?**
El repo tiene un `.gitignore` que excluye tus archivos personales (`context/about-me.md`, etc.).
Lo que sí se puede compartir: las skills, el Marco CAI y la estructura general.

**¿Qué pasa si me equivoco en el onboarding?**
Volvé a correr `/cabelma-onboard`. El sistema hace un backup de la versión anterior antes de sobreescribir.

---

## Versión

Cabelma-OS Launcher v1.0
