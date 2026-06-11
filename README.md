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

1. Cloná este repo y abrilo en tu AI
2. Pegá este prompt para arrancar el onboarding:

```
Leé el archivo de instrucciones de este repo y .claude/skills/cabelma-onboard/SKILL.md.
Ejecutá el proceso de onboarding: haceme las preguntas una a una, esperá mis respuestas,
y al terminar generá los archivos que indica. Empezá con la bienvenida del Paso 1.
```

> **Si usás Claude Code:** en lugar del prompt de arriba, escribí directamente `/cabelma-onboard`.

Cualquier AI de terminal funciona: Claude Code, Gemini CLI, Codex, u otro.
Cada uno lee su propio archivo de instrucciones (`CLAUDE.md`, `GEMINI.md` o `AGENTS.md`) — todos tienen el mismo contenido.

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
