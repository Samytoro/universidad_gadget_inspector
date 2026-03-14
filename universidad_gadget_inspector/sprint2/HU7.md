### HU-007 — Principio Open/Closed en la arquitectura de reglas de validación (B7)

**Como** arquitecta del sistema
**Quiero** que la nueva lógica contextual de validación se implemente como extensión (nueva clase) sin modificar el código existente
**Para** respetar el principio Open/Closed (SOLID), proteger los tests existentes y mantener la capacidad de agregar nuevas reglas en el futuro sin tocar las actuales

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que existe `RuleRequiredFields` con tests existentes aprobados, **When** se implementa `RuleRequiredFieldsForBacklog`, **Then** `RuleRequiredFields.apply()` no debe tener ninguna modificación **And** todos sus tests deben seguir pasando sin cambios |
| AC-2 | **Given** que `build_standard_rules()` es la única factory de reglas del sistema, **When** se actualiza para v2.0, **Then** debe retornar `[RuleRequiredFieldsForBacklog(), RuleFormatComoQuieroPara()]` **And** ningún otro componente del sistema debe necesitar conocer qué regla concreta se usa |
| AC-3 | **Given** que `UserStoryValidator` itera sobre `List[UserStoryRules]`, **When** recibe `RuleRequiredFieldsForBacklog` en lugar de `RuleRequiredFields`, **Then** debe funcionar sin cambios gracias al polimorfismo de la interfaz base **And** el comportamiento externo del endpoint `/validar` debe ser idéntico para HUs activas completas |

---
