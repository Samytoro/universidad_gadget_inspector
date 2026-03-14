### HU-006 — Mutation testing sobre la implementación de CRs (B6)

**Como** responsable de la calidad del proceso de testing
**Quiero** ejecutar mutation testing con `poodle` tras implementar los CRs
**Para** verificar que los tests realmente detectan cambios en la lógica crítica y no son solo tests de cobertura sin poder de detección

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que `poodle` se ejecuta sobre `src/app`, **When** finaliza el análisis, **Then** el resultado debe documentar el score global y el desglose por módulo **And** el score de `rule_required_fields_for_backlog.py` debe evaluarse específicamente como módulo central de los CRs |
| AC-2 | **Given** que `dynatrace_exporter.py` tiene bajo score de mutación, **When** se revisan los sobrevivientes, **Then** deben estar justificados como código de integración HTTP/logs que requiere tests de integración **And** no como lógica de negocio sin cubrir |
| AC-3 | **Given** que el score global queda documentado (56%, 538/960 mutantes), **When** se planifica la Fase III, **Then** los módulos con mayor número de sobrevivientes deben priorizarse en el backlog de mejora de tests **And** el reporte HTML debe estar disponible en `mutation_report/index.html` |

---
