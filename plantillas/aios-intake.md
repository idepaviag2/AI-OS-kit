# Intake del AIOS

Este es el archivo fuente-de-verdad de tu AIOS. Llénalo escribiendo, dictando, o
corriendo `/onboard` para una conversación guiada. Como sea que lo llenes, este es el
archivo que `/onboard` lee para armar tu configuración del Día 1.

**Tope duro: 7 preguntas.** Cada una se contesta en menos de 60 segundos. No lo pienses
de más — puedes editarlo y volver a correr `/onboard` cuando quieras.

---

## Q1 — ¿Quién eres, qué vendes y a quién se lo vendes?

Identidad, oferta, cliente ideal. Un párrafo de cada uno basta.

Si tu trabajo no es vender, contéstalo igual pero traducido: ¿qué produces, y quién
recibe lo que produces? El "cliente" puede ser interno — tu jefe, tu área, otro equipo.

```
[Tu respuesta aquí]
```

---

## Q2 — Pega 1 o 2 cosas que hayas escrito últimamente. No las edites.

Un correo, un post de LinkedIn, un mensaje, un documento — algo que suene a ti cuando
no estás tratando de sonar a nada.

**PÉGALAS TAL CUAL.** No las escribas aquí mientras platicas con Claude — las muestras
escritas dentro de la conversación salen contaminadas y son peores que no tener
ninguna. Abre tu correo o tu LinkedIn en otra pestaña y copia.

Idealmente dos: una personal y una de trabajo.

```
[Muestra 1 — pégala aquí]
```

```
[Muestra 2 — pégala aquí]
```

---

## Q3 — ¿Cuáles son tus 2 o 3 prioridades más grandes para los próximos 90 días?

Prioridades del trimestre. No aspiraciones del año. Cosas que, si no están hechas en 90
días, te van a hacer decir "desperdicié el trimestre".

**Cada una necesita un número, una fecha o un entregable.** "Crecer el negocio" no
cuenta. "Aprender" tampoco. "Dejar los cuatro reportes del área corriendo solos antes
del 30 de noviembre" sí.

```
[Tu respuesta aquí]
```

---

## Q4 — ¿Dónde cae el dinero realmente, y dónde se lleva el registro?

Se valen varias respuestas. ¿Stripe? ¿Transferencia al banco? ¿Un Excel? ¿El contador?
¿Un sistema contable? ¿Un sistema interno de la empresa?

Si no tocas dinero, contesta la versión equivalente: ¿cuál es el sistema donde vive la
operación que tú alimentas?

```
[Tu respuesta aquí]
```

---

## Q5 — ¿Dónde hablas con clientes, con tu equipo y con el mundo exterior, día a día?

¿Correo (cuál — Gmail, Outlook)? ¿WhatsApp? ¿Slack? ¿Teams? ¿Mensajes directos?
¿Teléfono? ¿Presencial?

Aprovecha y nombra a las personas clave: quién es tu jefe, con quién trabajas a diario,
quién es la contraparte externa. Tu asistente va a necesitar saber quién es quién.

```
[Tu respuesta aquí]
```

---

## Q6 — ¿Dónde viven las grabaciones de juntas, las notas y los documentos importantes?

¿Zoom? ¿Meet? ¿Google Drive? ¿OneDrive? ¿Notion? ¿Dropbox? ¿Un servidor? ¿Una carpeta del
escritorio que llevas meses queriendo ordenar?

Di también si las juntas **no** se graban. Eso suele ser el hueco más grande.

```
[Tu respuesta aquí]
```

---

## Q7 — ¿Cuál es la tarea que se te come la semana, y dónde llevas tus pendientes?

El mayor chupador de tiempo o la friega recurrente. Más dónde viven las tareas y
proyectos (Notion, Asana, ClickUp, una libreta, tu cabeza).

Si acabas de entrar al puesto y todavía no hay una friega consolidada, dilo así y
apunta lo que hoy te consume el tiempo. Se corrige en la próxima corrida.

```
[Tu respuesta aquí]
```

---

Cuando este archivo esté lleno, corre `/onboard` (o vuelve a correrlo) y el asistente
va a generar tu configuración del Día 1: `context/`, `references/voice.md`,
`connections.md` poblado y `CLAUDE.md` completo.
