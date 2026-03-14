### HU-005 — Tests unitarios: detección de backlog y validación contextual (B5)

**Como** desarrolladora responsable de la calidad del código
**Quiero** tests unitarios exhaustivos para la nueva regla `RuleRequiredFieldsForBacklog`
**Para** garantizar que la clasificación y la validación contextual funcionan correctamente y cualquier regresión futura sea detectada automáticamente

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que se ejecutan los 9 tests de `TestIsBacklog`, **When** se corren con `pytest -v`, **Then** todos deben pasar **And** deben cubrir: 7 estados backlog, iteración `None`, iteración vacía, iteración con "backlog" case-insensitive, y `state=None` |
| AC-2 | **Given** que se ejecutan los 7 tests de `TestValidacionBacklog`, **When** se corren, **Then** deben confirmar que título, descripción, criterios, prioridad y área son obligatorios **And** que `assigned_to` y `effort` son opcionales para cualquier HU en backlog |
| AC-3 | **Given** que se ejecutan los 5 tests de `TestValidacionActiva`, **When** se corren, **Then** deben confirmar que los 8 campos son obligatorios para HUs activas **And** que omitir cualquiera de ellos produce `apply() = False` |

---
