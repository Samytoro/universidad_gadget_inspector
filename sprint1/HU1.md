### HU-001 — Corrección de autenticación Azure DevOps

**Como** desarrolladora del equipo de calidad
**Quiero** que los clientes Azure DevOps usen autenticación Basic con el PAT en base64
**Para** poder conectarme correctamente a la organización sin recibir errores 401 Unauthorized

| # | Criterio de aceptación |
|---|---|
| AC-1 | **Given** que el sistema tiene un PAT configurado en `AZURE_TOKEN`, **When** `AzureDevOpsClient` se instancia, **Then** el header `Authorization` debe ser `Basic {base64(":PAT")}` **And** no debe contener la palabra `Bearer` en ninguna circunstancia |
| AC-2 | **Given** que los clientes `AzureDevOpsClient` y `AzureProjectsClient` construyen el header en `__init__`, **When** se realiza cualquier petición a la API de Azure DevOps, **Then** la respuesta debe ser `200 OK` con los work items solicitados **And** no debe aparecer ningún `401` en los logs |
| AC-3 | **Given** que `AZURE_TOKEN` o `AZURE_ORG_URL` no están configurados, **When** se intenta instanciar cualquier cliente Azure, **Then** debe lanzarse `ValueError` con mensaje descriptivo **And** no debe intentarse ninguna conexión de red antes de validar las variables |
| AC-4 | **Given** que los tests de headers existentes usaban `Bearer`, **When** se actualizan para reflejar `Basic`, **Then** `test_azure_client_extra.py`, `test_azure_projects_client.py` y `test_azure_client_mock.py` deben pasar sin modificar el código de producción más que los headers |

---

