### HU-009 — Campo `effort` opcional para HUs en Sprint Backlog (CR-003)

**Como** QA Lead del equipo
**Quiero** que el campo `Esfuerzo` (story points) no sea obligatorio para HUs en backlog
**Para** que HUs sin estimación en fase de refinamiento no sean marcadas como inválidas, respetando que el esfuerzo se define en el sprint planning y no antes

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que una HU tiene `state=New`, `effort=null` y cumple los 5 campos base, **When** el validador evalúa la HU, **Then** debe retornar `True` **And** `errors` debe ser `[]` |
| AC-2 | **Given** que una HU tiene `state=Committed`, `iteration="Sprint 5"` y `effort=null`, **When** el validador evalúa la HU, **Then** debe retornar `False` **And** `Microsoft.VSTS.Scheduling.Effort` debe estar en los campos reportados como faltantes |
| AC-3 | **Given** que una HU está en cualquiera de los 7 estados de backlog sin `effort`, **When** `_build_missing_fields` construye la lista de ausencias para Dynatrace, **Then** `Microsoft.VSTS.Scheduling.Effort` no debe aparecer en `MissingFields` **And** el campo `Valid` debe ser `"Sí"` si los demás campos base están completos |

---
