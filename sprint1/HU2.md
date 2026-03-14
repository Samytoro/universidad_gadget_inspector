### HU-002 — Protección de credenciales en el repositorio

**Como** desarrolladora responsable de la seguridad del proyecto
**Quiero** que el archivo `.env` con credenciales esté excluido del control de versiones
**Para** que los tokens de Azure DevOps y Dynatrace nunca sean expuestos accidentalmente en el repositorio

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que existe un archivo `.env` con `AZURE_TOKEN`, `AZURE_ORG_URL` y credenciales Dynatrace, **When** se ejecuta `git status` en el directorio del proyecto, **Then** el archivo `.env` no debe aparecer como tracked, staged ni untracked con intención de commit |
| AC-2 | **Given** que el repositorio tiene un `.gitignore`, **When** se lee el archivo, **Then** debe contener la entrada `.env` de forma explícita **And** también debe incluir variantes como `.env.local` para prevención proactiva |
| AC-3 | **Given** que un desarrollador nuevo clona el repositorio, **When** ejecuta `git log --all --full-history -- .env`, **Then** no debe existir ningún commit que contenga credenciales en texto plano **And** el README debe indicar cómo crear el `.env` local desde `.env.example` |

---
