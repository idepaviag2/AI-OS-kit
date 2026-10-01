# AIOS — Sistema Operativo de IA sobre Claude Code

Un kit que convierte a Claude Code en tu **Sistema Operativo de IA personal**: un
asistente que conoce tu negocio, alcanza tus herramientas, sabe hacer tu trabajo y
eventualmente corre sin que se lo pidas.

**¿Vas empezando? No leas esto todavía. Abre `EMPIEZA-AQUI.md`.**

Este documento es el *por qué* detrás del kit — los dos frameworks y la arquitectura.
Léelo cuando quieras entender qué estás construyendo.

---

## La prueba de fuego

> **"Mientras no estás en tu escritorio, tu AIOS observa un evento real del mundo y
> produce un resultado más rápido y más preciso que el que producirías tú."**

Cada decisión de diseño de este kit apunta a eso. Si una capa, una skill o una
plantilla no contribuye a esa prueba, no entra.

---

## Cómo sabes que está funcionando

No hay una métrica objetiva. Hay tres señales que aparecen solas en tu semana:

**1. Alguien de tu equipo te busca.**
> Un compañero te escribe con una duda. Te das cuenta de que tu AIOS la contestaría
> mejor, más rápido y con las fuentes exactas — aunque tú estuvieras despierto y libre.
> Así que le preguntas a tu AIOS también. Ese es el momento en que dejas de ser el
> cuello de botella de tu propio conocimiento.

**2. Dejas de brincar entre pestañas.**
> Cuando llega algo nuevo, tu primer movimiento es preguntarle al AIOS, no abrir seis
> cosas. La superficie default para pensar cambia. Silencioso. Se acumula.

**3. El conocimiento se te sale de la cabeza.**
> Dejas de intentar recordar datos del negocio. No repasas qué decidiste el trimestre
> pasado ni qué dijo el cliente en esa junta. Confías en la recuperación. El AIOS
> guarda la verdad, tú guardas las preguntas.

---

## Dos frameworks

**Primero las 3Ms, luego las 4Cs.** Sin el cambio de cabeza, la arquitectura es nada
más una estructura de carpetas.

### Las Tres Ms — cerebro de operador (cómo piensas)

| M | En una línea |
|---|---|
| **Mindset** | Default Shift, Desglose por Funciones, Regla de la Curiosidad. *¿Hasta qué punto se puede apalancar la IA aquí?* |
| **Método** | Encuentra el cuello de botella → EAD (Eliminar, Automatizar, Delegar) → Mapea el proceso → Elige nivel de autonomía → Amárralo a un número. |
| **Máquina** | Principio Lego, Cadena de Validación, Método de la Bici, Regla del Interno, Interruptor de Apagado. *Lo aburrido es hermoso. Los flujos le ganan a los agentes.* |

Desglose completo en `references/3ms-framework.md`. La skill `/level-up` te camina las
tres cada semana.

> *The Three Ms of AI™ es marca registrada de Nate Herk. © 2026 Nate Herk.*

### Las Cuatro Ces — arquitectura (qué construyes)

| # | Capa | En una línea | Prueba de "esta capa ya está" |
|---|---|---|---|
| 1 | **Contexto** | Conoce tu negocio | Una sesión nueva contesta "¿qué hace este negocio y quién trabaja aquí?" sin buscar nada |
| 2 | **Conexiones** | Alcanza tus cosas | "¿Qué tengo mañana en el calendario y qué tareas vencen?" → datos en vivo, sin pegar nada |
| 3 | **Capacidades** | Sabe hacer el trabajo | Una frase corta dispara un flujo de varios pasos que produce un entregable |
| 4 | **Cadencia** | Corre sin que se lo pidan | Laptop cerrada. Llega un resumen. Alguien le escribe y recibe una respuesta real |

**Contexto no se salta.** Conexiones y Capacidades pueden construirse en paralelo.
Cadencia va al final — no automatices flujos que no funcionan a mano.

> *The Four Cs of an AIOS™ es marca registrada de Nate Herk. © 2026 Nate Herk.*

---

## Qué trae — 3 skills

El kit es deliberadamente flaco. Las skills que trae son herramientas de pensamiento,
no automatizaciones pesadas. Tú construyes encima.

| Skill | Tipo | Cuándo correrla |
|---|---|---|
| `/onboard` | Asistente de arranque (una vez) | Día 1. Entrevista de 7 preguntas. Genera tus archivos base y llena `CLAUDE.md`. |
| `/audit` | Skill recurrente | Día 7 y luego cada semana. Reporte de huecos por las 4Cs. Solo lectura. |
| `/level-up` | Skill recurrente | Día 14 y luego cada semana. Entrevista de las 3Ms. Una corrida = una cosa construida. |

`/audit` pregunta *"¿está bien construido el AIOS?"* (forma). `/level-up` pregunta
*"¿qué palanca de negocio me estoy perdiendo?"* (función). Trabajan en serie: primero
arregla la estructura, después la planeación de capacidades tiene sentido.

---

## Estructura de la carpeta

```
AI-OS/
├── EMPIEZA-AQUI.md                  ← El protocolo. Empieza por aquí.
├── GUARDRAILS.md                    ← Reglas duras de operación
├── README.md                        ← Este archivo
├── CLAUDE.md                        ← Tu manual de operación (lo llena /onboard)
├── EXPANSIONS.md                    ← Qué agregar conforme creces
├── LICENSE
├── .gitignore
├── aios-intake.md                   ← Fuente de verdad de /onboard. Edítalo y re-corre.
├── connections.md                   ← Registro de todo lo que tu AIOS alcanza
├── context/                         ← Sobre ti y tu negocio (lo llena /onboard)
├── references/
│   └── 3ms-framework.md             ← El cerebro de operador
├── decisions/
│   └── log.md                       ← Registro de qué se decidió y por qué
├── archives/                        ← Lo viejo. No se borra: se mueve aquí.
└── .claude/
    └── skills/
        ├── onboard/SKILL.md
        ├── audit/SKILL.md
        └── level-up/SKILL.md
```

Ver `EXPANSIONS.md` para qué agregar conforme creces (`projects/`, `templates/`,
`scripts/`, `.claude/agents/`, sub-OS por vertical, etc.).

---

## Licencia y atribución

Licencia MIT. Kit base © 2026 Nate Herk.

*The Three Ms of AI™* y *The Four Cs of an AIOS™* son marcas de Nate Herk. Ambos
frameworks vienen en este repo con atribución. Úsalos libremente; no los reempaquetes
como propios.

`EMPIEZA-AQUI.md` y `GUARDRAILS.md` son añadidos de campo — reglas sacadas de operar un
AIOS en producción con acceso de escritura a sistemas reales.
