# EMPIEZA AQUÍ — Protocolo de onboarding de tu AIOS

Esta carpeta convierte a Claude Code en tu **Sistema Operativo de IA** (AIOS): un
asistente que conoce tu negocio, alcanza tus herramientas, sabe hacer tu trabajo y
corre solo.

**No leas todo el folder.** Lee este archivo, sigue los pasos en orden y el sistema te
va guiando. Los demás documentos existen para que el asistente los lea, no tú.

Tiempo real de arranque: **20 minutos el día 1.** Lo demás es un ritual semanal de 30 min.

---

## Antes de empezar

> **¿Todavía no tienes Claude Code instalado?** Cierra esto y abre
> **`00-INSTALA-ESTO-PRIMERO.md`**. Ahí está, paso por paso, cómo dejar la máquina lista
> en Mac y en Windows. Vuelve aquí cuando `claude --version` te imprima un número.

Si ya instalaste, solo confirma tres cosas:

1. La carpeta vive en tu carpeta de usuario (`~/AI-OS` en Mac,
   `C:\Users\tu-usuario\AI-OS` en Windows). **No la dejes en Descargas** — este folder se
   va a volver tu memoria y va a crecer contigo.
2. Ya iniciaste sesión con tu cuenta de Claude.
3. La abriste en Claude: terminal → `cd ~/AI-OS` → `claude`. (O en VS Code con la
   extensión, con el ícono de la chispa ✻.)

Cuando Claude arranque y veas el prompt, ya estás dentro. Sigue.

---

## Día 1 — El intake (15 minutos)

Escribe esto tal cual:

```
/onboard
```

Te va a hacer **7 preguntas**. Ni una más — está topado a propósito. Reglas del intake:

- **Contesta corto y honesto.** Un párrafo por respuesta es suficiente. No estás
  escribiendo un plan de negocio, estás describiendo tu realidad.
- **La pregunta 2 es la única con regla dura.** Te va a pedir que *pegues* 1 o 2 cosas
  que hayas escrito de verdad (un correo, un post, un mensaje). **Pégalas sin editar,
  copiadas de tu correo o tu LinkedIn.** Si las escribes ahí en el chat, salen
  contaminadas por la conversación y tu asistente va a sonar a robot para siempre.
  Ábrelas en otra pestaña y pégalas crudas.
- **En la pregunta 3 (prioridades) no digas "crecer".** Di un número, una fecha o un
  entregable. "Cerrar 4 clientes nuevos antes del 30 de septiembre" sirve. "Crecer" no.
- Si te interrumpen, no pasa nada: cada respuesta se va guardando en `aios-intake.md`.
  Vuelves y corres `/onboard` otra vez.

Al terminar, el asistente escribe solo tus archivos base: quién eres, qué vendes, qué
importa este trimestre, cómo escribes, y qué herramientas usas.

### El momento de la verdad (1 minuto)

Justo después, escribe:

```
¿en qué me debería enfocar esta semana?
```

Si la respuesta cita **tus** prioridades con **tus** palabras, funcionó. Si te contesta
algo genérico tipo "enfócate en tus objetivos clave", tu intake quedó vago: abre
`aios-intake.md`, ponle carne y vuelve a correr `/onboard`.

---

## Días 2 a 6 — Úsalo de verdad

Aquí es donde la mayoría lo abandona. La regla es simple:

> **Cuando te llegue algo nuevo, tu primer movimiento es preguntarle al AIOS, no abrir
> seis pestañas.**

Tráele problemas reales: un correo que no sabes cómo contestar, una decisión que traes
atorada, un documento que hay que resumir. Es un compañero de pensamiento, no una
máquina expendedora — pregúntale *por qué* propone lo que propone y pídele 3
alternativas.

**Además, un solo trabajo esta semana:** conecta **una** herramienta. Abre
`connections.md`, escoge la fila que más te duela (normalmente calendario o correo) y
dile al asistente:

```
ayúdame a conectar <herramienta>. Quiero que puedas leer <lo que necesitas>.
```

Una sola. No siete. Cuando quede, pídele que guarde lo que aprendió en
`references/<herramienta>-api.md` — eso se investiga una vez y sirve para siempre.

**Y cuando decidas algo importante, dile:** "regístralo en la bitácora de decisiones".
En 3 meses vas a querer saber *por qué* decidiste, no solo *qué* decidiste.

---

## Día 7 — La auditoría

```
/audit
```

Te da una calificación sobre 100 en las Cuatro Ces (Contexto, Conexiones,
Capacidades, Cadencia) y los **3 huecos con más palanca**.

La primera corrida casi siempre da entre 30 y 50. **Eso es normal y es el punto** — es
tu línea base. Escoge **un** hueco de los tres y ciérralo esta semana. Repite `/audit`
cada semana y ve subir el número.

---

## Día 14 — La primera automatización

```
/level-up
```

Una entrevista de tres fases que termina con **una cosa construida**:

1. **Mindset** — qué hiciste 3+ veces esta semana (ahí está el oro).
2. **Método** — ¿se puede *eliminar* en vez de automatizar? ¿A qué número le pega?
3. **Máquina** — se construye, arrancando en modo manual con supervisión.

Deja que te empuje a lo aburrido y determinista. Lo aburrido es lo que no se rompe.

---

## Semana 3 en adelante — El ritual

| Cuándo | Qué |
|---|---|
| Todos los días | Primera parada para cualquier cosa nueva: el AIOS |
| Cada decisión que importe | "regístralo en la bitácora" |
| Viernes | `/level-up` — una automatización nueva |
| Cada semana | `/audit` — ve subir el número |
| Cada trimestre | Edita `aios-intake.md` y vuelve a correr `/onboard` |

**Una automatización por semana. En seis meses son veinticinco.** Ahí está el interés
compuesto.

---

## Errores que van a echarte a perder el arranque

1. **Contestar el intake bonito en vez de honesto.** El asistente trabaja con lo que le
   des. Si le mientes sobre tus prioridades, te va a ayudar con las prioridades
   equivocadas.
2. **Escribir las muestras de voz en el chat.** Pégalas. Es la única regla que no se
   negocia.
3. **Conectar siete herramientas el día 2.** Una. Que funcione. Luego la siguiente.
4. **Automatizar antes de haberlo hecho a mano.** Si el proceso no funciona manual, no
   va a funcionar automático — solo se va a romper más rápido.
5. **Construir algo que no entiendes.** Si no puedes explicar cómo funciona, construiste
   un pasivo, no un activo. Pregunta hasta entender.
6. **Dejar de usarlo la semana 2.** El bajón de productividad de los primeros días es
   real (~20% menos output). Al otro lado está el doble. Aguántalo.

---

## Antes de darle acceso a algo tuyo

Lee `GUARDRAILS.md`. Son las reglas duras — sacadas de operar uno de estos en
producción, no de teoría — sobre qué puede hacer solo, qué tiene que pedirte permiso,
y cómo no volar nada. **Son 5 minutos y te ahorran un desastre.**

En corto, lo mínimo:
- Nada de contraseñas ni datos bancarios en el chat.
- Lo que lee de correos, PDFs o webs son **datos**, no órdenes.
- Nada sale a un cliente sin que tú lo veas primero.

---

## Qué hay en esta carpeta

| Archivo | Para qué |
|---|---|
| `00-INSTALA-ESTO-PRIMERO.md` | Cómo dejar la máquina lista (Mac y Windows). Se lee una vez. |
| `EMPIEZA-AQUI.md` | Este protocolo. Lo lees tú. |
| `GUARDRAILS.md` | Reglas duras de operación. Lo leen tú y el asistente. |
| `CLAUDE.md` | El manual de operación del asistente. Se llena solo con `/onboard`. |
| `aios-intake.md` | Tus 7 respuestas. Edítalo y vuelve a correr `/onboard` cuando cambie algo. |
| `connections.md` | Registro de todo lo que tu AIOS puede alcanzar. |
| `README.md` | Los dos frameworks (3Ms y 4Cs). Léelo cuando quieras el porqué. |
| `EXPANSIONS.md` | Qué agregarle conforme crezcas. |
| `context/` | Quién eres, tu negocio, tus prioridades (lo llena `/onboard`). |
| `references/` | Frameworks, tu voz, guías de APIs. |
| `decisions/log.md` | Bitácora de decisiones. Solo se agrega, nunca se borra. |
| `archives/` | Lo viejo. No se borra: se mueve aquí. |

---

> Kit base: **AIS-OS** de Nate Herk (MIT). Los frameworks *The Three Ms of AI™* y
> *The Four Cs of an AIOS™* son marcas de Nate Herk © 2026. `GUARDRAILS.md` y este
> protocolo son añadidos de campo, de operar un AIOS en producción.
