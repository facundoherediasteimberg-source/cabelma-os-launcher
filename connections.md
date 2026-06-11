# Sistemas y herramientas

> Este archivo se completa automáticamente al correr `/cabelma-onboard`.
> Editalo directamente cuando agregues o cambies una conexión.

| # | Sistema / Herramienta | Uso | Mecanismo AI | Auth | Última revisión |
|---|---|---|---|---|---|
| 1 | | | — | — | — |

---

## Sistemas disponibles en Cabelma (referencia)

| Sistema | Para qué sirve | Cómo accede el AI |
|---|---|---|
| Softland ERP | Gestión central: producción, compras, stock, finanzas | UI automation (PAD/PowerShell) o scripts |
| Excel | Análisis y reportes | Generación de fórmulas, VBA, scripts Python |
| Power BI | Visualización y dashboards | Via API o exportación |
| Claude Code | AI de trabajo | CLAUDE.md (este repo) |
| Gemini CLI | AI de trabajo | GEMINI.md (este repo) |
| Codex CLI | AI de trabajo | AGENTS.md (este repo) |

## Cómo conectar una herramienta

1. Agregá una fila en la tabla de arriba
2. En "Mecanismo AI": `script` / `MCP` / `API` / `manual` / `UI automation`
3. Guardá las credenciales en `.env` (nunca acá)
4. Actualizá "Última revisión" con la fecha
