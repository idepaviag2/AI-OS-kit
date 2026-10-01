# EXPANSIONES — qué agregar conforme creces

El kit viene flaco a propósito. Tres skills, seis carpetas, un framework de referencia.
Ya. Conforme lo uses vas a rebasar la base — esta guía te dice qué agregar, cuándo y
por qué.

La estructura de tu AIOS debe verse como un negocio chico bien llevado. No como el
sótano de un acumulador.

---

## Qué trae el kit (no lo quites)

| Carpeta / archivo | Para qué |
|---|---|
| `context/` | Sobre ti, tu negocio, tus prioridades. Lo llena `/onboard`. |
| `references/` | Frameworks, muestras de voz, guías de API, procedimientos. |
| `decisions/log.md` | Registro que solo crece: qué se decidió y por qué. |
| `archives/` | Archivos viejos. No se borran: se mueven aquí. |
| `connections.md` | Registro de todo sistema que tu AIOS alcanza. |
| `GUARDRAILS.md` | Reglas duras de operación. |
| `.claude/skills/` | Tus skills: `/onboard`, `/audit`, `/level-up`. Agrega más vía `/level-up`. |
| `aios-intake.md` | Fuente de verdad de `/onboard`. Edítalo y re-corre cuando quieras. |
| `CLAUDE.md` | Manual de operación raíz. Lo llena `/onboard`. Edítalo cuando cambie tu rol o tu voz. |

---

## Qué agregar conforme creces

| Carpeta / archivo | Agrégalo cuando | Por qué |
|---|---|---|
| `projects/` | Traigas 2+ frentes activos con su propio contexto | Los proyectos vivos necesitan contexto acotado, aparte de los archivos permanentes de `context/` |
| `templates/` | Te cachas copiando y pegando los mismos prompts o esqueletos | Puntos de partida reutilizables; reduce la deriva |
| `brand-assets/` | Generes contenido visual (carruseles, láminas, miniaturas) | Centraliza logos, paletas, tipografías, tono — el AIOS lo toma de ahí en vez de adivinar |
| `references/sops/` | Documentes cómo corren tus procesos recurrentes | Procedimientos que el AIOS lee para ejecutar consistente |
| `references/{herramienta}-api.md` | Conectes una API o MCP nueva y descubras cómo funciona | Se investiga una vez y sirve para siempre. `/audit` lo premia; las skills futuras no lo re-investigan. |
| `scripts/` | Escribas Python o Bash para pegarle a APIs sin MCP | La segunda conexión de casi todos es un script, no un MCP |
| `.claude/agents/` | Necesites un sub-asistente para investigación o redacción repetible | Los agentes corren en su propio contexto — tu sesión principal se mantiene ligera |
| Sub-OS (ej. `youtube-os/`) | Tengas una vertical con sus propios datos, hojas, transcripciones | Patrón de aislamiento: cada vertical con su manual y sus skills |

---

## Cadencias sugeridas

- `decisions/log.md` — cada decisión que importe (`/level-up` las captura solo)
- `archives/` — limpieza trimestral: proyectos muertos, skills deprecadas, intakes viejos
- `references/sops/` — cuando alguien nuevo tenga que correr un proceso, escribe el procedimiento
- `connections.md` — cada vez que conectes algo, agrega la fila
- `references/{herramienta}-api.md` — al mismo tiempo que la fila de arriba
- `CLAUDE.md` — revisión trimestral; reescribe la sección de prioridades

---

## Qué NO agregar

Anti-patrones. Se ven útiles y pudren la estructura:

- **No vacíes archivos crudos de correo o chat en `references/`.** Esto no es un
  basurero de documentos. Solo hechos ya interpretados.
- **No armes carpetas dentro de carpetas por teatro organizacional.** Plano con buenos
  nombres le gana a anidado. Si necesitas jerarquía para encontrar algo, tienes un
  problema de búsqueda, no de organización.
- **No agregues `notas/`, `varios/`, `tmp/` ni `inbox/`.** Son cementerios. Si es viejo
  va a `archives/`; si es nuevo, escribe un archivo real en el lugar correcto.
- **No pre-crees carpetas que no necesitas.** Las carpetas vacías son ruido.
- **No tengas dos bitácoras de decisiones en paralelo.** Una: `decisions/log.md`.
- **No bifurques tu manual de operación.** Un solo `CLAUDE.md` en la raíz. Los sub-OS
  pueden tener el suyo acotado, pero la raíz es la canónica.
- **No crees un segundo documento de plan.** Ver `GUARDRAILS.md`, punto 3. Este es el
  error que más silenciosamente te va a costar.

---

## Cómo saber que ya toca agregar una carpeta

Tres preguntas:

1. **¿Esto es conceptualmente nuevo?** ¿O cabe en algo que ya existe?
2. **¿Voy a tocarlo 3+ veces el próximo mes?** Si no, es prematuro.
3. **¿`/level-up` podría meter una skill futura aquí de forma natural?** Si sí, el
   sistema lo va a usar. Si no, estás organizando para ti, no para el sistema.

Dos síes = agrégalo. Un sí = espera.

---

> *La estructura de tu AIOS debe verse como un negocio chico bien llevado, no como el
> sótano de un acumulador. Cuando no encuentres algo, esa es la señal de consolidar, no
> de agregar otra carpeta.*
