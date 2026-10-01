# Conexiones

Registro de todo sistema que tu AIOS puede alcanzar. Lo llena `/onboard` con las
respuestas Q4-Q7; se expande conforme conectas herramientas nuevas. `/audit` revisa
este archivo para medir cobertura y frescura.

**El Día 1 es normal que las siete filas digan `sin conectar`.** Eso no es un problema,
es la línea base. Se conecta **una por semana**, empezando por la que desbloquee un
entregable del trimestre.

| # | Dominio | Herramienta | Mecanismo | Auth | Última revisión |
|---|---|---|---|---|---|
| 1 | Ingresos / Finanzas | | sin conectar | — | — |
| 2 | Interacciones con clientes | | sin conectar | — | — |
| 3 | Calendario | | sin conectar | — | — |
| 4 | Comunicación | | sin conectar | — | — |
| 5 | Proyectos / tareas | | sin conectar | — | — |
| 6 | Inteligencia de juntas | | sin conectar | — | — |
| 7 | Conocimiento / archivos | | sin conectar | — | — |

**Mecanismos posibles:** `mcp` (servidor MCP o conector de Claude), `script`
(Python/Bash pegándole a una API, en `scripts/`), `export` (volcado de CSV/JSON),
`key+ref` (llave en `.env` + guía en `references/{herramienta}-api.md`), `archivo local`,
`sin conectar`.

**Regla:** cuando conectes una herramienta nueva, guarda también
`references/{herramienta}-api.md` con los endpoints, el flujo de autenticación y las
consultas comunes. Se investiga una vez, sirve para siempre — y las skills futuras no
lo vuelven a investigar.

**Las credenciales no van aquí.** En esta tabla se anota *dónde* vive la llave (`.env`,
gestor de contraseñas, llavero del sistema), nunca la llave misma. Ver `GUARDRAILS.md`,
punto 4.
