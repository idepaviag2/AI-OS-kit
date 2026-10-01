# Instalación en Mac

La guía principal del kit (`00-INSTALA-ESTO-PRIMERO.md`) está escrita para Windows, porque
es el sistema de la persona a la que se le entregó primero. Este archivo guarda los pasos
equivalentes para **macOS**, para quien monte el kit en una Mac.

Es el mismo recorrido y el mismo orden. Solo cambian los comandos y el instalador.

**Requisitos:** macOS 13 o superior, 4 GB de RAM, internet, y una suscripción pagada de
Claude (Pro, Max, Team o Enterprise). El plan gratuito de claude.ai no incluye Claude Code.

---

## 1. Abre la Terminal

`Cmd + Espacio` → escribe `Terminal` → Enter. Pegar es `Cmd + V`; cada comando se ejecuta
con Enter.

## 2. Instala Claude Code

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Cuando termine, **cierra la Terminal y ábrela otra vez** (si no la reabres, el siguiente
comando falla aunque la instalación haya salido bien). Luego:

```bash
claude --version
```

Tiene que imprimir un número de versión. Si dice `command not found: claude`, la
instalación quedó pero la Mac todavía no sabe dónde buscarla.

Esta instalación se actualiza sola en segundo plano.

## 3. Instala Visual Studio Code y la extensión de Claude

Baja VS Code de **https://code.visualstudio.com**. Se descarga un `.zip`: ábrelo y
**arrastra el ícono a la carpeta de Aplicaciones** (si lo dejas en Descargas se porta
raro). Ábrelo una vez para que macOS te pregunte si confías en la app.

Dentro de VS Code: `Cmd + Shift + X` → busca **Claude Code** → la de **Anthropic**
(`anthropic.claude-code`) → **Install**.

## 4. Baja el kit y ponlo en `~/AI-OS`

Acepta primero la invitación al repositorio privado que te llegó por correo.

**Opción A — ZIP (la que no falla).** Abre
**https://github.com/idepaviag2/AI-OS-kit** → botón verde **Code** → **Download ZIP**.
Descomprime, renombra la carpeta de `AI-OS-kit-main` a `AI-OS` y muévela a tu carpeta de
usuario (`/Users/tu-usuario/AI-OS`). No la dejes en Descargas.

**Opción B — git.** Ojo: en Mac, `git clone` por HTTPS sobre un repo **privado** pide
usuario y contraseña, y **GitHub ya no acepta contraseñas**. Hace falta un token, o la
herramienta oficial de GitHub, que resuelve el login desde el navegador:

```bash
brew install gh        # si no tienes Homebrew, usa la opción A
gh auth login          # GitHub.com → HTTPS → autenticar en el navegador
cd ~
gh repo clone idepaviag2/AI-OS-kit AI-OS
```

## 5. Pon las plantillas en su lugar

```bash
cd ~/AI-OS
cp plantillas/aios-intake.md aios-intake.md
cp plantillas/CLAUDE.md CLAUDE.md
cp plantillas/connections.md connections.md
cp plantillas/decisions-log.md decisions/log.md
```

El por qué de este paso está explicado en `plantillas/LEEME.md`.

## 6. Entra a tu cuenta y arranca

```bash
cd ~/AI-OS
claude
```

La primera vez se abre el navegador para iniciar sesión. O desde VS Code:
`Archivo → Abrir carpeta…` → `AI-OS`, y abre Claude con el ícono de la chispa ✻.

## 7. Verifica

```bash
claude doctor
```

Después de eso, el resto del recorrido es idéntico: abre `EMPIEZA-AQUI.md`, corre
`/onboard`, y lee `GUARDRAILS.md` antes de conectarle nada tuyo.
