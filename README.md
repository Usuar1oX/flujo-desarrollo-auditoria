# flujo-desarrollo-auditoria

Skill de Muse que documenta el flujo completo de trabajo entre Antonio
(dueño), Muse (planeación y auditoría) y el agente desarrollador
(Antigravity, Claude Code u otro): pedir → planear entre los tres →
construir en pruebas → auditar en vivo → corregir → re-auditar →
producción → cerrar.

Nació de la operación real de DescuenTips, CRONomiX, PoS Pues y OdontoMX
(nov 2026), donde lograr que las conexiones funcionaran tomó días de
intentos — incluidas varias rutas que se abrieron y no sirvieron.

## Contenido

| Archivo | Qué guarda |
|---|---|
| `SKILL.md` | La instrucción maestra: roles, principios y el ciclo paso a paso. |
| `CONDITIONS_TEMPLATE.md` | Plantilla de condiciones de satisfacción medibles y verificables. |
| `ISSUE_TEMPLATE.md` | Formatos «Listo para auditar», veredicto de auditoría y hallazgo nuevo. |
| `CHECKLIST.md` | Checklist permanente de auditoría: funcional, datos, visual/responsive, técnica y cierre. |
| `CHANNELS.md` | Los canales que sí funcionan: SSH/GCP, timbre tmux, ACP (solo opiniones), GitHub sin tarjetas, vigilantes. |
| `DEAD_ENDS.md` | Rutas ya probadas que no funcionan y su condición de reintento. |

## Uso en un proyecto nuevo

1. Clonar el repo y habilitar a Muse el acceso SSH al servidor.
2. Leer `CHANNELS.md` y `DEAD_ENDS.md` antes de improvisar rutas.
3. Crear el entorno de pruebas ligero y el issue n.º 1 con el protocolo.
4. Correr una primera tanda pequeña de punta a punta.
