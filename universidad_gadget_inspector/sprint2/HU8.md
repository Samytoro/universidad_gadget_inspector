### HU-008 — Campo `assigned_to` opcional para HUs en Sprint Backlog (CR-002)

**Como** QA Lead del equipo
**Quiero** que el campo `Asignado a` no sea obligatorio para HUs en backlog
**Para** que HUs recién creadas o en refinamiento no sean marcadas como inválidas por no tener asignación, lo que generaba falsos negativos en el reporte de Dynatrace

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que una HU tiene `state=New`, `assigned_to=null` y cumple los 5 campos base (título, descripción, criterios, prioridad, área), **When** `RuleRequiredFieldsForBacklog.apply(us)` evalúa la HU, **Then** debe retornar `True` **And** `errors` debe ser `[]` |
| AC-2 | **Given** que una HU tiene `state=Active`, `iteration="Sprint 5"` y `assigned_to=null`, **When** el validador evalúa la HU, **Then** debe retornar `False` **And** el mensaje de error debe indicar campos requeridos, confirmando que CR-002 no aplica a HUs activas |
| AC-3 | **Given** que una HU en backlog sí tiene `assigned_to` asignado y no vacío, **When** el validador evalúa la HU, **Then** debe retornar `True` **And** el campo opcional presente no debe generar ningún error ni warning |
| AC-4 | **Given** que `run_validation.py` construye el dict de resultados para Dynatrace, **When** procesa una HU de backlog sin `assigned_to`, **Then** `Valid` debe ser `"Sí"` **And** `System.AssignedTo` no debe aparecer en el campo `MissingFields` |

---
