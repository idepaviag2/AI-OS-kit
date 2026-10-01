---
name: onboard
description: Úsala el Día 1 de una instalación de AIOS, cuando alguien diga "configúrame", "hazme el onboarding", "vamos a empezar", "llena mi AIOS", o acabe de copiar el kit. Asistente combinado — corre la entrevista de 7 preguntas Y genera los archivos base al final. Idempotente — se puede volver a correr después de editar aios-intake.md.
---

## Qué hace esta skill

Un solo asistente combinado. Lee o escribe `aios-intake.md` (el intake canónico),
conduce la entrevista de 7 preguntas si el archivo no está lleno, y al final genera los
archivos base del Día 1. No hay una skill separada de scaffolding — esto es un solo
flujo.

**El momento wow:** al terminar, sugiere el prompt de cierre *"Pruébalo — pregúntame:
¿en qué me debería enfocar esta semana?"*. La persona lo corre una vez. Ese es el wow.
No existe una skill `/today` que guardar — el prompt mismo siembra el framework de
Mindset (el Default Shift) para que lo interiorice.

## Cuándo NO correr esto

- Si ya hizo onboarding y quiere refrescar: sí corre, pero salta las preguntas ya
  contestadas (es idempotente).
- Si quiere agregar una conexión nueva: eso no es onboarding — mándalo a editar
  `connections.md` directo, o a agendar una caminata de `/level-up` fase 2.

## Ejecución

### Paso 1: Lee el intake

Lee `aios-intake.md`. Revisa qué secciones Q1-Q7 tienen contenido vs. el marcador
`[Tu respuesta aquí]`.

- **Todas llenas** → salta el Paso 2, brinca al Paso 3 (generar archivos).
- **Algunas llenas** → pregúntale: "Veo que Q1, Q3 y Q4 ya están contestadas. ¿Llenamos
  las demás ahora, o genero los archivos con lo que hay?" Es su decisión.
- **Ninguna llena (copia fresca)** → corre el Paso 2 conversacionalmente.

### Paso 2: La entrevista (7 preguntas, tope duro)

Pregunta de una en una. Escribe cada respuesta en `aios-intake.md` conforme avanzas
(para que pueda retomar si lo interrumpen).

**Q1 — ¿Quién eres, qué vendes y a quién se lo vendes?**
Identidad, oferta, cliente ideal. Un párrafo de cada uno basta.

**Q2 — Pega 1 o 2 cosas que hayas escrito últimamente. No las edites.**
*Esta es la única pregunta con regla dura.* Las muestras de voz TIENEN que pegarse, no
escribirse en la conversación. Si empieza a escribir prosa fresca, recházalo:

> *"Espérate — pégalo crudo. Si lo escribes aquí mientras platicamos, la muestra ya
> viene moldeada por nuestra conversación. Abre tu último correo o tu post de LinkedIn
> en otra pestaña y pega el texto sin editar. Esta es la única regla que no puedo
> doblar."*

Pide dos muestras. Un correo y un post. O dos de cualquiera.

**Q3 — ¿Cuáles son tus 2 o 3 prioridades más grandes para los próximos 90 días?**
Prioridades trimestrales. Empújale si dice "crecer el negocio" — que nombre un número,
una fecha o un entregable.

**Q4 — ¿Dónde cae el dinero realmente, y dónde se lleva el registro?**
Se valen varias respuestas. Mapea al Dominio 1 (Ingresos/Finanzas).

**Q5 — ¿Dónde hablas con clientes, con tu equipo y con el mundo exterior día a día?**
Correo (Gmail/Outlook), WhatsApp, Slack/Teams/Discord, mensajes directos. Mapea a los
Dominios 2 y 4.

**Q6 — ¿Dónde viven las grabaciones de juntas, las notas y los documentos importantes?**
Mapea a los Dominios 6 y 7.

**Q7 — ¿Cuál es la tarea que se te come la semana, y dónde llevas tus pendientes?**
Captura el dolor principal (lo usa `/level-up` el Día 14) + Dominio 5 (tareas).

El Dominio 3 (Calendario) se infiere de Q5: Gmail → Google Calendar; Outlook → Outlook
Calendar. Confírmalo en el Paso 3.

### Paso 3: Genera los archivos base del Día 1

Una vez completo el intake, genera estos archivos (o actualízalos si es re-corrida).
Respalda los originales en `archives/intake-{AAAA-MM-DD-HHMM}/` si ya existían.

1. **`context/sobre-mi.md`** — de Q1 (identidad, rol) + Q7 (dolor principal). Un párrafo
   corto de cada uno.
2. **`context/sobre-el-negocio.md`** — de Q1 (oferta, cliente ideal) + Q4 (modelo de
   ingresos). Un párrafo.
3. **`context/prioridades.md`** — de Q3. Lista numerada, una línea por prioridad.
4. **`references/voice.md`** — de Q2. Pega las muestras tal cual con un encabezado corto
   que explique su uso ("Iguala este registro al redactar; no imites mi voz en contenido
   externo sin enseñarme el borrador antes").
5. **`connections.md`** — llena las 7 filas con las respuestas Q4-Q7. Cada fila queda con
   `mecanismo: sin conectar`, `auth: —`, `última revisión: —`. La persona conecta el
   Día 2.
6. **`CLAUDE.md`** — llena todos los marcadores `{{...}}`. Sustituye el nombre, la
   prioridad declarada, un resumen del registro de voz y un resumen breve de conexiones.

### Paso 4: La pantalla de cierre

Imprime una sola pantalla. Máximo tres líneas:

```
✓ Día 1 listo. Tu AIOS ya sabe quién eres, qué vendes, qué importa este trimestre y
  cómo suenas.

Hoy: pregúntame — "¿en qué me debería enfocar esta semana?"
Mañana: escoge UNA herramienta de connections.md y conéctala.
Día 7: corre /audit para ver tu calificación.
```

Cuando corra el prompt de cierre ("¿en qué me debería enfocar esta semana?"), responde
usando SOLO los archivos de contexto nuevos. Pega:
- Lista de 3 viñetas de prioridad, en el registro de voz de Q2
- Cada viñeta amarrada a una prioridad declarada en Q3
- Línea final: *"Si tuviera que escoger una cosa para el lunes, sería [X], porque
  [razón sacada de las prioridades]. ¿Quieres que redacte el primer correo? Y —
  ¿dónde aplica aquí el Default Shift? ¿Hasta qué punto se puede apalancar la IA en
  esta tarea?"*

La pregunta del Default Shift siembra el framework de Mindset antes de que `/level-up`
lo introduzca formalmente el Día 14.

## Reglas críticas de implementación

1. **El tope de 7 preguntas no se negocia.** No agregues una Q8 en la conversación.
2. **La muestra de voz no se puede saltar.** Si escribe las muestras en el chat,
   recházalo y dile que pegue de algo que ya escribió.
3. **Generación de un solo tiro.** Al terminar el Paso 2, escribe los archivos del Paso
   3 en un solo lote. Sin confirmaciones de ida y vuelta. Se itera editando
   `aios-intake.md` y volviendo a correr.
4. **Idempotente.** Re-correr con el intake editado refresca los archivos de contexto;
   respalda originales en `archives/intake-{ts}/`. Salta preguntas ya contestadas salvo
   que quiera revisarlas.
5. **La pantalla de cierre son tres líneas.** No es un menú.
6. **No generes skills extra.** No hagas `/today`, `/draft`, `/connect`, etc. El kit
   trae 3 skills; las demás se escriben vía `/level-up`.
7. **Solo lectura en `references/3ms-framework.md` y `GUARDRAILS.md`.** Ya vienen en el
   kit. No los sobreescribas.
8. **Nada de escribir en `.env`.** No pidas llaves de API el Día 1. Las conexiones van
   el Día 2.

## Verificación (para quien implemente)

- Prueba en frío: copia un kit fresco, corre `/onboard`, llena las 7 respuestas, corre
  la generación, haz el prompt wow. La respuesta debe citar Q1 + Q3 + Q7
  específicamente. Genérico = falla.
- Idempotencia: re-corre `/onboard` con una prioridad de Q3 cambiada. Esperado: solo
  `context/prioridades.md` y la sección de prioridades de `CLAUDE.md` se actualizan;
  respaldo creado en `archives/intake-{ts}/`.
- Rechazo de voz: escribe una muestra en el chat. Esperado: la skill lo rechaza y pide
  que pegue.

> *Adaptado de The Three Ms of AI™ © 2026 Nate Herk. El lenguaje de Mindset de la
> pantalla de cierre viene de `references/3ms-framework.md`.*
