### HU-003 — Captura de métricas baseline del sistema v1.0

**Como** responsable del proyecto de mantenimiento
**Quiero** tener documentadas las métricas de calidad del sistema antes de cualquier cambio de la Fase II
**Para** poder comparar objetivamente el antes y después y demostrar la mejora entregada

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que el sistema v1.0 tiene tests existentes, **When** se ejecuta `pytest --cov` sobre el código base, **Then** las métricas deben quedar documentadas como baseline: 75 tests, 97% cobertura, 389 statements, 12 sin cubrir **And** 58 warnings de deprecación Pydantic v2 |
| AC-2 | **Given** que el baseline está capturado, **When** al final de la Fase II se mide con las mismas herramientas, **Then** debe ser posible calcular el delta de mejora en CC promedio (objetivo: bajar de 4.475 a ≤ 3.5), cobertura (objetivo: mantener ≥ 95%) y duplicación (objetivo: 0%) |
| AC-3 | **Given** que las métricas baseline están documentadas en el CHANGELOG, **When** un stakeholder revisa el progreso del proyecto, **Then** debe encontrar los números iniciales y finales con evidencias ejecutables (comandos reproducibles) **And** los porcentajes de mejora calculados |

---
