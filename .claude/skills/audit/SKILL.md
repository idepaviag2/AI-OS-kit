---
name: audit
description: Úsala cuando alguien pida una auditoría de su AIOS, quiera calificar su setup contra las Cuatro Ces, o diga "¿está funcionando mi AIOS?" / "audita mi setup" / "encuéntrale los huecos a mi AIOS". Produce un tablero de las Cuatro Ces con los 3 arreglos de mayor palanca.
---

## Qué hace esta skill

Corre la **auditoría de las Cuatro Ces** sobre el proyecto actual de Claude Code. Lee
(nunca escribe) el manual de operación, la memoria, las skills, los agentes, los MCPs,
las decisiones y las referencias. Califica cada C sobre 25. Saca las fortalezas y los 3
huecos con más palanca, con el siguiente paso concreto de cada uno.

**El alcance es estructural — "¿está bien construido el AIOS?"** NO es un planeador de
capacidades. Los huecos de capacidad ("podrías construir un resumen diario si conectaras
el calendario") le tocan a `/level-up`. La auditoría contesta: ¿están en buena forma los
archivos, carpetas, registros y conexiones?

La primera corrida es la línea base. Re-córrela cada semana para ver subir el número.
Ese es el gancho del interés compuesto.

## Contexto de hoy

- **Fecha:** !`date +%Y-%m-%d`
- **Raíz del proyecto:** el directorio de trabajo actual

## Las Cuatro Ces (25 puntos cada una = 100)

| Capa | Prueba |
|---|---|
| **Contexto** | Conoce el negocio — identidad, equipo, voz, decisiones, referencias |
| **Conexiones** | Alcanza las cosas de la persona — MCPs, integraciones, fuentes de datos |
| **Capacidades** | Sabe hacer el trabajo — skills + agentes |
| **Cadencia** | Corre sin que se lo pidan — agendas, hooks, rituales recurrentes |

## Ejecución

### Paso 1: Descubre la forma del proyecto

La auditoría busca **patrones e intención**, no rutas exactas. Los nombres de archivo
varían. Usa Glob y Read para revisar:

**Manual de operación:** `CLAUDE.md` (raíz), `CLAUDE.local.md`.
**Memoria:** `MEMORY.md` (raíz), `~/.claude/projects/<id>/memory/MEMORY.md`, o carpeta
`memory/`.
**Skills:** `.claude/skills/*/SKILL.md` — cuenta + frontmatter.
**Agentes:** `.claude/agents/*.md` — cuenta + frontmatter.
**Mecanismos de conexión** (cualquiera de estos cuenta como "alcanzable"):
- MCPs: `.mcp.json`, `.claude/settings.json` (llave mcpServers), `.claude/settings.local.json`
- Scripts de API: `scripts/*.py|.js|.ts` documentados en `CLAUDE.md`
- Pipelines de exportación: `data/`, `imports/`, `exports/` con script de refresco y
  fecha de última corrida
- Llaves de API + guía: entradas en `.env` + su `references/{herramienta}-api.md`

**Registro de conexiones:** `connections.md` (donde sea).
**Guías de referencia:** `references/{herramienta}-api.md`, `references/*-reference.md`.
**Decisiones:** `decisions/log.md`, `decisions.md`, o cualquier bitácora que solo crezca.
**Referencias / procedimientos:** carpetas `references/`, `docs/`, `sops/`.
**Plantillas:** `templates/`, `.claude/templates/`.
**Hooks / trabajos agendados:** llave `hooks` en `.claude/settings.json`, o skills que se
llamen `morning-*`, `weekly-*`, `daily-*`, `monthly-*`, `standup`, o sus equivalentes en
español (`diario-*`, `semanal-*`, `brief-*`).

No penalices por nombres no canónicos si la intención está capturada en otro lado.

### Paso 2: Califica cada C (25 puntos cada una)

#### Contexto (25 pts)

| Criterio | Puntos | Cómo detectarlo |
|---|---|---|
| Manual de operación existe y es sustancioso (>200 palabras) | 5 | Lee `CLAUDE.md`, cuenta palabras |
| Identidad / rol / voz capturados | 5 | `CLAUDE.md` menciona quién es la persona + rol/misión, o existe `.claude/rules/*.md` |
| Memoria persistente con varias entradas | 5 | `MEMORY.md` con >3 entradas, o `memory/` con >3 archivos |
| Documentos de referencia existen | 5 | `references/`, `docs/` o `sops/` tiene ≥1 archivo |
| Decisiones capturadas | 5 | `decisions/log.md` o equivalente tiene ≥1 entrada |

#### Conexiones (25 pts) — por dominio, agnóstico al mecanismo

Una conexión cuenta como "alcanzable" por CUALQUIER mecanismo: MCP, script, pipeline de
exportación, o llave en `.env` + `references/{herramienta}-api.md`. El kit es
API-primero; la auditoría no prefiere MCPs.

**Los 7 dominios universales de datos:**

| # | Dominio | Ejemplos |
|---|---|---|
| 1 | Ingresos / Finanzas | Stripe, banco, QuickBooks, Contpaqi, Excel del contador |
| 2 | Interacciones con clientes | HubSpot, Salesforce, WhatsApp Business, correo como CRM |
| 3 | Calendario | Google Calendar, Outlook, Calendly |
| 4 | Comunicación | Gmail, Outlook, Slack, Teams, WhatsApp |
| 5 | Proyectos / tareas | ClickUp, Asana, Linear, Notion, Jira |
| 6 | Inteligencia de juntas | Granola, Otter, Fireflies, Zoom, Meet |
| 7 | Conocimiento / archivos | Notion, Drive, Dropbox, SharePoint, NAS |

**Bonus:** llaves de API de servicios de IA, historial de decisiones, publicación de
contenido.

| Criterio | Puntos | Cómo detectarlo |
|---|---|---|
| Cobertura de dominios | 10 | 1.4 pts por dominio alcanzable. Redondea a 0.5. Tope 10. |
| Guías de referencia presentes | 5 | -1 por herramienta conectada sin `references/{herramienta}-api.md`. Piso 0. |
| Frescura de auth / pipeline | 5 | -1 por conexión en estado `necesita-auth`/`expirada`, o script sin corrida en 30 días. Piso 0. |
| Documentado en `connections.md` | 3 | 0 si falta; 1 escaso; 2 la mayoría; 3 cubre todo lo alcanzable. |
| Balance lectura-Y-escritura | 2 | Al menos una conexión puede ESCRIBIR (mandar correo, publicar, etc.). 0 si todo es solo lectura — entonces el AIOS es un visor, no un sistema operativo. |

#### Capacidades (25 pts)

| Criterio | Puntos | Cómo detectarlo |
|---|---|---|
| 3+ skills instaladas | 10 | Cuenta `.claude/skills/*/SKILL.md` |
| 1+ skill hecha por la persona | 10 | Nombres de skill que no sean: `onboard`, `audit`, `level-up`, `skill-creator`, `skill-builder` (las canónicas del kit + las de fábrica) |
| 1+ agente definido | 5 | Cuenta `.claude/agents/*.md` ≥ 1 |

#### Cadencia (25 pts)

| Criterio | Puntos | Cómo detectarlo |
|---|---|---|
| 1+ disparador recurrente o agendado | 10 | Hooks en `.claude/settings.json`, o nombre de skill tipo `diario-*` / `semanal-*` / `daily-*` / `weekly-*` |
| Señal de actividad reciente | 10 | Archivos en `.claude/skills/` modificados en los últimos 30 días, o entrada en `decisions/log.md` de los últimos 30 días |
| Carpeta de plantillas poblada | 5 | `templates/` o `.claude/templates/` con ≥1 archivo |

### Paso 3: Identifica los 3 huecos de mayor palanca

Por cada criterio que perdió puntos: palanca = (puntos perdidos) × (multiplicador de
impacto).

**Multiplicadores:**
- 0 dominios alcanzables: **4x** (el AIOS está ciego al negocio)
- Manual de operación ausente o flaco: **3x** (es el cimiento)
- ≤2 dominios alcanzables: **3x** (Conexiones es la puerta a los datos vivos)
- 0 skills: **2x** (sin Capacidades no hay AIOS)
- Sin disparador recurrente: **2x** (sin Cadencia no hay autonomía)
- Todas las conexiones de solo lectura: **2x** (es un visor, no un sistema)
- 0 guías de referencia para herramientas conectadas: **1.5x** (cada skill futura
  re-investiga las mismas APIs)
- Sin bitácora de decisiones: **1.5x**
- Todos los demás: **1x**

Ordena por palanca descendente. Toma los 3 primeros. Para cada uno, escribe un siguiente
paso concreto de una línea:
- **¿Falta una skill?** "Escribe `SKILL.md` en `.claude/skills/<nombre>/SKILL.md` con
  frontmatter YAML" (o usa `skill-creator` si está disponible).
- **¿Falta registrar una decisión?** "Agrega una entrada a `decisions/log.md`."
- **¿Falta alcanzar un dominio?** Prefiere API+script (escribe `scripts/{herramienta}_api.py`
  y guarda `references/{herramienta}-api.md`). Recomienda `claude mcp add` solo si no hay
  camino por API.
- **¿Herramienta conectada sin guía?** "Investiga la API una vez y guarda endpoints,
  auth y consultas comunes en `references/{herramienta}-api.md`."
- **¿Falta disparador recurrente?** "Agrega un hook a `.claude/settings.json`, o escribe
  una skill `diario-*` que corras cada mañana."

### Paso 4: Imprime el reporte

Directo en el chat (Markdown). Formato:

```
# Auditoría del AIOS — {fecha}
**Calificación: {total}/100** ({etapa})

Umbrales de etapa:
- 0-39 → Etapa 0: Cimientos
- 40-69 → Etapa 1: Construido
- 70-89 → Etapa 2: Compuesto
- 90-100 → Etapa 3: Autónomo

## Tablero

Contexto       {barra}  {n}/25  {etiqueta}
Conexiones     {barra}  {n}/25  {etiqueta}
Capacidades    {barra}  {n}/25  {etiqueta}
Cadencia       {barra}  {n}/25  {etiqueta}

(barra = ## por cada 5 pts; etiqueta = "Fuerte" ≥20, "Sólido" 15-19, "Flaco" 8-14,
"Ausente" <8)

## Fortalezas
- {1-3 viñetas cortas de los criterios mejor calificados}

## Top 3 huecos (por palanca)
1. **{hueco}** (-{puntos} × {multiplicador})
   → {siguiente paso concreto}
2. ...
3. ...

## Siguiente sugerido: {la acción de mayor palanca}

---
Solo huecos estructurales. Para explorar huecos de CAPACIDAD (qué podría HACER tu AIOS
que todavía no puede), corre /level-up después de esta auditoría.
```

### Paso 5: Ofrece guardar el reporte

Después de imprimirlo, pregunta: "¿Guardo esta auditoría en `audits/audit-{fecha}.md`
para poder ver la calificación en el tiempo?" Si dice que sí, escríbelo (crea `audits/`
si no existe). Ese es el único efecto de escritura.

## Notas

- **Solo lectura por default.** Nunca modifiques `CLAUDE.md`, memoria, skills ni ningún
  archivo del proyecto. La única escritura opcional es el reporte.
- **Sé flexible con los nombres de archivo.** No penalices por nombres no canónicos si la
  intención está capturada.
- **Sé honesto, no generoso.** Un 95/100 es un logro presumible. La mayoría de los setups
  caen entre 40 y 70.
- **No sugieras skills que no existen.** Apunta a lo que de verdad está disponible.
- **La velocidad importa.** Reporte en menos de 60 segundos. Lee archivos puntuales,
  cuenta carpetas de skills sin leer cada una completa (solo frontmatter).
- **La detección de Cadencia es difusa.** Infiere de los nombres de skill si los hooks no
  están limpios.
