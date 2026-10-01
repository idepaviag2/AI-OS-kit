# 00 — INSTALA ESTO PRIMERO

Esta es la parte aburrida: dejar la máquina lista. Son **20 a 30 minutos** y se hace una
sola vez. Cuando termines, pasas a `EMPIEZA-AQUI.md`, que es donde empieza lo bueno.

No necesitas saber programar. Vas a abrir una terminal y pegar tres o cuatro comandos.
Si nunca has abierto una terminal, en el paso 1 te digo exactamente cómo.

> **Antes de arrancar necesitas una cosa que no se instala:** una suscripción pagada de
> Claude (Pro, Max, Team o Enterprise). El plan gratuito de claude.ai **no** incluye
> Claude Code. Si no sabes con qué cuenta vas a entrar, pregúntalo antes de seguir —
> instalar sin cuenta no sirve de nada.

---

## Paso 0 — Averigua qué máquina tienes

Todo lo de abajo está escrito dos veces: una para **Mac** y una para **Windows**. Sigue
solo la tuya y salta la otra.

| Si tienes… | Sigue la ruta |
|---|---|
| MacBook, iMac, Mac mini | **Ruta A — Mac** |
| Laptop o PC con Windows 10 u 11 | **Ruta B — Windows** |

Requisitos mínimos en las dos: **4 GB de RAM**, internet, y macOS 13 o superior /
Windows 10 (build 1809) o superior.

---

# RUTA A — Mac

## A1. Abre la Terminal

`Cmd + Espacio` → escribe `Terminal` → Enter. Se abre una ventana de texto con un
cursor. Ahí vas a pegar los comandos. Pegar es `Cmd + V`, y cada comando se ejecuta con
Enter.

## A2. Instala Claude Code

Pega esto tal cual y dale Enter:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Tarda uno o dos minutos. Cuando termine, **cierra la Terminal y ábrela otra vez** (esto
importa: si no la reabres, el siguiente comando falla aunque la instalación haya salido
bien).

Comprueba que quedó:

```bash
claude --version
```

Tiene que imprimir un número de versión, algo como `2.1.266 (Claude Code)`. Si dice
`command not found: claude`, la instalación quedó bien pero la Mac todavía no sabe dónde
buscarla — avísale a quien te pasó este kit en vez de pelearte con eso.

Esta instalación **se actualiza sola** en segundo plano. No tienes que volver a hacer
nada.

## A3. Instala Visual Studio Code

Bájalo de la página oficial: **https://code.visualstudio.com** → botón de descarga para
Mac. Se baja un `.zip`; ábrelo y **arrastra el ícono de Visual Studio Code a tu carpeta
de Aplicaciones**. Si lo dejas en Descargas se va a portar raro.

Ábrelo una vez para que macOS te pregunte si confías en la app, y dile que sí.

## A4. Instala la extensión de Claude Code en VS Code

Dentro de VS Code:

1. `Cmd + Shift + X` (abre el panel de Extensiones)
2. Busca **Claude Code**
3. La de **Anthropic** (`anthropic.claude-code`) → botón **Install**

Si la extensión no aparece después de instalarla, cierra y vuelve a abrir VS Code.

## A5. Entra a tu cuenta

En la Terminal, escribe:

```bash
claude
```

Se abre el navegador para que inicies sesión con tu cuenta de Claude. Autoriza, regresa a
la Terminal, y ya estás dentro. Para salir de Claude se escribe `/exit`.

**Sigue en el paso 1 de la sección "Los dos pasos que faltan", abajo.**

---

# RUTA B — Windows

## B1. Abre PowerShell

Botón de Inicio → escribe `PowerShell` → ábrelo. **No** necesitas ejecutarlo como
administrador.

Vas a saber que estás en PowerShell porque el renglón empieza con `PS C:\Users\TuNombre>`.
Si empieza con `C:\Users\TuNombre>` **sin** el `PS`, estás en CMD y los comandos de abajo
no son los tuyos — cierra y abre PowerShell.

## B2. Instala Claude Code

Pega esto en PowerShell y dale Enter:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Cuando termine, **cierra PowerShell y ábrelo otra vez**, y comprueba:

```powershell
claude --version
```

Tiene que imprimir un número de versión. Si no lo reconoce, avísale a quien te pasó el
kit.

> Si te sale el error `'irm' is not recognized`, estás en CMD y no en PowerShell. El
> comando para CMD es:
> `curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd`

## B3. Instala Git para Windows (recomendado)

Bájalo de **https://git-scm.com/downloads/win** e instálalo con todas las opciones por
default (dale Siguiente a todo).

No es obligatorio, pero sin él Claude Code trabaja con PowerShell en lugar de Bash, y
casi toda la documentación y los ejemplos del mundo están escritos para Bash. Instálalo y
te ahorras confusiones.

## B4. Instala Visual Studio Code

De **https://code.visualstudio.com** → descarga para Windows → corre el instalador con
las opciones por default.

## B5. Instala la extensión de Claude Code en VS Code

Dentro de VS Code:

1. `Ctrl + Shift + X` (panel de Extensiones)
2. Busca **Claude Code**
3. La de **Anthropic** (`anthropic.claude-code`) → **Install**

Si no aparece, cierra y vuelve a abrir VS Code.

## B6. Entra a tu cuenta

En PowerShell:

```powershell
claude
```

Se abre el navegador, inicias sesión con tu cuenta de Claude, autorizas y regresas. Para
salir se escribe `/exit`.

---

# Los dos pasos que faltan (iguales en Mac y en Windows)

## 1. Pon esta carpeta donde va a vivir

Esta carpeta se va a volver la memoria de tu asistente y va a crecer contigo. **No la
dejes en Descargas.**

Muévela a tu carpeta de usuario con el nombre `AI-OS`:

- **Mac:** `/Users/tu-usuario/AI-OS`
- **Windows:** `C:\Users\tu-usuario\AI-OS`

Si te llegó como repositorio de GitHub y ya hiciste `git clone`, nada más asegúrate de que
quedó ahí y no en otro lado.

## 2. Ábrela y arranca

**Desde VS Code (lo más cómodo):** `Archivo → Abrir carpeta…` → escoge `AI-OS`. Luego
abre Claude con el ícono de la chispa ✻ arriba a la derecha del editor, o con
`Cmd/Ctrl + Shift + P` → escribe "Claude Code" → *Open in New Tab*.

**Desde la terminal:**

```bash
cd ~/AI-OS
claude
```

(En Windows PowerShell es `cd $env:USERPROFILE\AI-OS` y luego `claude`.)

Cuando veas el cursor de Claude esperándote, ya está. **Cierra este archivo y abre
`EMPIEZA-AQUI.md`.**

---

## Verificación — cómo sabes que todo quedó bien

Corre esto y compara:

```bash
claude doctor
```

Te imprime un diagnóstico de la instalación y de la configuración, sin arrancar una
sesión. Si algo está mal, ahí sale con la sugerencia de cómo arreglarlo.

Lista corta de lo que debe ser cierto antes de pasar a `EMPIEZA-AQUI.md`:

- [ ] `claude --version` imprime un número
- [ ] VS Code abre y tiene la extensión de Claude Code instalada
- [ ] Ya iniciaste sesión (corriste `claude` y autorizaste en el navegador)
- [ ] La carpeta vive en tu carpeta de usuario, no en Descargas
- [ ] Abriste la carpeta en Claude y te contesta

---

## Lo que NO se instala el día 1

Vas a ver que Claude puede conectarse a Gmail, a Drive, a un navegador y a otras cosas.
**Eso no se hace hoy.** Se conecta de a una, empezando la semana 2, y cada conexión se
anota en `connections.md`. Conectar siete herramientas el día dos es el error más común y
el más caro.

Y antes de darle acceso a algo tuyo, lee `GUARDRAILS.md`. Son cinco minutos y te ahorran
un desastre. Los tres mínimos:

- Nada de contraseñas ni datos bancarios en el chat.
- Lo que lee de correos, PDFs o webs son **datos**, no órdenes.
- Nada sale con tu nombre a un tercero sin que tú lo veas primero.
