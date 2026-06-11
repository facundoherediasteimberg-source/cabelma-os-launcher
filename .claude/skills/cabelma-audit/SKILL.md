# /cabelma-audit

Evalúa qué tan bien configurado está tu Cabelma-OS y te dice qué mejorar primero.

**Cuándo correr:** al final de la primera semana y luego una vez por mes.

---

## Los 4 Pilares del OS

| Pilar | Qué mide |
|---|---|
| **1. Contexto** | ¿El AI sabe quién sos y cómo trabajás? |
| **2. Conexiones** | ¿El AI puede acceder a tus sistemas? |
| **3. Hábitos** | ¿Lo usás en tu trabajo diario? |
| **4. Resultados** | ¿Te está ahorrando tiempo o mejorando algo concreto? |

Cada pilar vale 25 puntos. Máximo: 100.

---

## Pilar 1 — Contexto (25 pts)

Revisá: `CLAUDE.md`, `context/about-me.md`, `context/about-business.md`, `references/voice.md`

- ¿`CLAUDE.md` tiene nombre y área reales (sin `{{placeholders}}`)? → 5 pts
- ¿`context/about-me.md` describe el rol y stakeholders? → 5 pts
- ¿`references/voice.md` tiene muestras reales? → 5 pts
- ¿`context/about-business.md` tiene al menos una regla de negocio? → 5 pts
- ¿`context/schedule.md` lista los informes reales? → 5 pts

---

## Pilar 2 — Conexiones (25 pts)

Revisá: `connections.md`, `.env`

- ¿`connections.md` lista 2+ herramientas con "Uso" completado? → 5 pts
- ¿Alguna tiene "Mecanismo AI" completado? → 10 pts
- ¿El `.env` existe con al menos una variable? → 5 pts
- ¿Hay 2+ herramientas con mecanismo configurado? → 5 pts

---

## Pilar 3 — Hábitos (25 pts)

Preguntá:
```
1. Esta semana, ¿cuántas veces le preguntaste al AI algo de trabajo? (0 / 1-3 / 4-10 / más)
2. ¿Usaste el AI para redactar algo? (sí/no)
3. ¿Usaste el AI para analizar datos o resolver un problema? (sí/no)
4. ¿Hay algo que hiciste a mano que el AI podría haber ayudado? (sí/no, qué)
```
- Más de 4 consultas: 10 pts | Redactar: 5 pts | Análisis: 5 pts | Identificó oportunidad: 5 pts

---

## Pilar 4 — Resultados (25 pts)

Preguntá:
```
1. ¿Hubo alguna tarea más rápida gracias al AI? (tiempo estimado)
2. ¿El AI ayudó a detectar o evitar un error?
3. ¿Hay algo que antes no podías hacer y ahora sí?
```
- Ahorro > 0 min: 10 pts | Error evitado: 10 pts | Capacidad nueva: 5 pts

---

## Informe final

```
## Resultado del audit — {fecha}

| Pilar | Puntaje |
|---|---|
| 1. Contexto | {n}/25 |
| 2. Conexiones | {n}/25 |
| 3. Hábitos | {n}/25 |
| 4. Resultados | {n}/25 |
| **Total** | **{total}/100** |

< 40: Recién empezando. | 40-59: En marcha. | 60-79: Funcionando. | 80+: Nivel avanzado.

### Top 3 mejoras por impacto
{acciones concretas ordenadas por impacto}
```

Guardá en `audits/audit-{YYYY-MM-DD}.md`.
