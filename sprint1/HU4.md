### HU-004 — Identificación automática de HUs en Sprint Backlog (CR-001)

**Como** miembro del equipo de calidad
**Quiero** que el sistema identifique automáticamente si una Historia de Usuario está en Sprint Backlog
**Para** poder aplicar reglas de validación diferenciadas según el ciclo de vida real de la HU y no rechazar HUs que legítimamente no tienen todos los campos completos

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que una HU tiene `state` igual a cualquiera de `New`, `Proposed`, `Approved`, `Planned`, `To Do`, `DoR Validation` u `On Hold`, **When** `is_backlog(us)` evalúa la HU, **Then** debe retornar `True` **And** debe hacerlo sin importar el valor de la iteración asignada |
| AC-2 | **Given** que una HU tiene `iteration` igual a `None`, cadena vacía, o contiene la palabra `"backlog"` en cualquier combinación de mayúsculas/minúsculas (ej: `"Product Backlog"`, `"BACKLOG"`, `"Mi backlog sprint"`), **When** `is_backlog(us)` evalúa la HU, **Then** debe retornar `True` **And** debe hacerlo sin importar el estado |
| AC-3 | **Given** que una HU tiene `state=Active` e `iteration="Sprint 5"` (ninguna condición de backlog se cumple), **When** `is_backlog(us)` evalúa la HU, **Then** debe retornar `False` **And** el sistema debe aplicar la validación activa completa de 8 campos |
| AC-4 | **Given** que `state=None`, **When** `is_backlog(us)` evalúa la HU, **Then** debe retornar `True` por defecto **And** la HU debe validarse con los requisitos mínimos de backlog para no ser rechazada por ausencia de estado |

---
