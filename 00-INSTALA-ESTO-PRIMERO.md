# 00 — INSTALA ESTO PRIMERO (Windows)

Esta es la parte aburrida: dejar la máquina lista. Son **20 a 30 minutos** y se hace una
sola vez. Cuando termines, pasas a `EMPIEZA-AQUI.md`, que es donde empieza lo bueno.

No necesitas saber programar. Vas a abrir una ventana de texto y pegar tres o cuatro
comandos. Cada paso dice exactamente qué pegar y qué tiene que salir.

> **Antes de arrancar necesitas una cosa que no se instala:** una suscripción pagada de
> Claude (Pro, Max, Team o Enterprise). El plan gratuito de claude.ai **no** incluye
> Claude Code. Si no sabes con qué cuenta vas a entrar, pregúntalo antes de seguir —
> instalar sin cuenta no sirve de nada.

**Requisitos:** Windows 10 (build 1809) o superior, 4 GB de RAM, internet.

*(Esta guía está escrita para Windows. Si en algún momento alguien monta el kit en una
Mac, los pasos equivalentes están en `extras/instalacion-en-mac.md`.)*

---

## 1. Abre PowerShell

Botón de Inicio → escribe `PowerShell` → ábrelo. **No** necesitas ejecutarlo como
administrador.

Vas a saber que estás en el lugar correcto porque el renglón empieza con
`PS C:\Users\TuNombre>`. Si empieza con `C:\Users\TuNombre>` **sin** el `PS`, estás en
CMD, que es otra cosa: cierra y abre PowerShell.

Para pegar en PowerShell: `Ctrl + V`. Cada comando se ejecuta con Enter.

---

## 2. Instala Claude Code

Pega esto y dale Enter:

```powershell
irm https://claude.ai/install.ps1 | iex
```

Tarda uno o dos minutos. Cuando termine, **cierra PowerShell y ábrelo otra vez.** Esto
importa: si no lo reabres, el siguiente comando falla aunque la instalación haya salido
bien.

Comprueba que quedó:

```powershell
claude --version
```

Tiene que imprimir un número de versión, algo como `2.1.266 (Claude Code)`.

- Si dice que no reconoce `claude`, la instalación quedó pero Windows todavía no sabe
  dónde buscarla — avísale a quien te pasó este kit en vez de pelearte con eso.
- Si sale `'irm' is not recognized`, estabas en CMD y no en PowerShell. Regresa al paso 1.

Esta instalación **se actualiza sola** en segundo plano. No tienes que volver a hacer nada.

---

## 3. Instala Git para Windows

Bájalo de **https://git-scm.com/downloads/win** e instálalo dándole Siguiente a todo, sin
cambiar nada.

No es estrictamente obligatorio, pero instálalo: sin él Claude Code trabaja con PowerShell
en lugar de Bash, y casi todos los ejemplos y la documentación del mundo están escritos
para Bash. Además es lo que hace que el paso 5 (bajar el kit con git) funcione sin
complicaciones.

---

## 4. Instala Visual Studio Code y la extensión de Claude

**4a.** Baja VS Code de **https://code.visualstudio.com** → botón de descarga para Windows
→ corre el instalador con las opciones por default.

**4b.** Ábrelo y agrega la extensión:

1. `Ctrl + Shift + X` (abre el panel de Extensiones)
2. Busca **Claude Code**
3. La de **Anthropic** (`anthropic.claude-code`) → botón **Install**

Si la extensión no aparece después de instalarla, cierra y vuelve a abrir VS Code.

---

## 5. Baja el kit y ponlo donde va a vivir

Esta carpeta se va a volver la memoria de tu asistente y va a crecer contigo. Va en tu
carpeta de usuario, **`C:\Users\tu-usuario\AI-OS`**. No la dejes en Descargas.

El kit vive en un repositorio privado de GitHub. Primero **acepta la invitación que te
llegó por correo** (necesitas cuenta de GitHub; es gratis). Luego escoge una de las dos:

### Opción A — descargar el ZIP (la que no falla)

1. Abre **https://github.com/idepaviag2/AI-OS-kit**
2. Botón verde **Code** → **Download ZIP**
3. Descomprime el ZIP y **renombra la carpeta a `AI-OS`** (el ZIP la nombra
   `AI-OS-kit-main`)
4. Muévela a `C:\Users\tu-usuario\AI-OS`

Cuatro clics y listo. La única desventaja es que no te llegan solas las correcciones que
se le hagan al kit después; para eso está la opción B, y la puedes dejar para cuando ya
estés cómodo.

### Opción B — clonar con git

Más limpia a la larga, porque te deja traer actualizaciones con `git pull`. En Windows
funciona directo, porque Git para Windows trae un gestor de credenciales que abre el
navegador solo:

```powershell
cd $env:USERPROFILE
git clone https://github.com/idepaviag2/AI-OS-kit.git AI-OS
```

El `AI-OS` del final es a propósito: la carpeta se llama así aunque el repo se llame
`AI-OS-kit`.

> **Si te atoras aquí, no le dediques más de diez minutos: usa la opción A y sigue.**
> Bajar el kit no es la parte importante.

---

## 6. Pon las plantillas en su lugar

El kit trae cuatro archivos vacíos en la carpeta `plantillas/`. Hay que copiarlos a la
raíz una sola vez. En PowerShell:

```powershell
cd $env:USERPROFILE\AI-OS
Copy-Item plantillas\aios-intake.md aios-intake.md
Copy-Item plantillas\CLAUDE.md CLAUDE.md
Copy-Item plantillas\connections.md connections.md
Copy-Item plantillas\decisions-log.md decisions\log.md
```

Si prefieres no pegar comandos, abre la carpeta en Claude (paso 7) y pídeselo así:
*"copia las cuatro plantillas de `plantillas/` a su lugar, según `plantillas/LEEME.md`"*.

> **Por qué este paso existe:** en cuanto llenas esos cuatro archivos contienen tu
> información real — nombres de personas, sistemas internos, tus prioridades, muestras de
> tu forma de escribir. El `.gitignore` del kit excluye las versiones de la raíz a
> propósito, para que lo que escribas se quede en tu máquina y no se suba a GitHub. Las
> copias de `plantillas/` están vacías y por eso sí viajan. Detalle en
> `plantillas/LEEME.md`.

---

## 7. Entra a tu cuenta y arranca

**Desde VS Code (lo más cómodo):** `Archivo → Abrir carpeta…` → escoge
`C:\Users\tu-usuario\AI-OS`. Luego abre Claude con el ícono de la chispa ✻ arriba a la
derecha del editor, o con `Ctrl + Shift + P` → escribe "Claude Code" → *Open in New Tab*.

**Desde PowerShell:**

```powershell
cd $env:USERPROFILE\AI-OS
claude
```

La primera vez se abre el navegador para que inicies sesión con tu cuenta de Claude.
Autoriza, regresa, y ya estás dentro. Para salir se escribe `/exit`.

Cuando veas el cursor de Claude esperándote, ya está. **Cierra este archivo y abre
`EMPIEZA-AQUI.md`.**

---

## Verificación — cómo sabes que todo quedó bien

Corre esto:

```powershell
claude doctor
```

Te imprime un diagnóstico de la instalación y de la configuración sin arrancar una sesión.
Si algo está mal, ahí sale con la sugerencia de cómo arreglarlo.

Antes de pasar a `EMPIEZA-AQUI.md`, esto tiene que ser cierto:

- [ ] `claude --version` imprime un número
- [ ] Git para Windows instalado
- [ ] VS Code abre y tiene la extensión de Claude Code
- [ ] La carpeta está en `C:\Users\tu-usuario\AI-OS`, no en Descargas
- [ ] Los cuatro archivos de `plantillas/` ya están copiados a su lugar
- [ ] Ya iniciaste sesión (corriste `claude` y autorizaste en el navegador)
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
