# Fathom AI: Text-to-SQL generation-only starter

This service produces **UNVALIDATED SQL**. It does not connect to PostgreSQL or execute SQL. Do not execute generated SQL until explicit schema allowlisting, SQLGlot validation, row-level authorization, read-only DB role, timeouts and result limits are implemented.

## Endpoints
- GET /health
- POST /generate-sql: {"question":"...", "schema_description":"..."}

## Local Docker build (PowerShell)
```powershell
docker build -t fathom-ai:0.1.0 .
```

## Kubernetes environment
Existing ConfigMap `fathom-ai-config`: LITELLM_BASE_URL, LITELLM_MODEL.
Existing Secret `fathom-ai-secrets`: LITELLM_API_KEY.
Do not embed either key in the image.

## Next step
Publish image to a registry reachable by Kubernetes (e.g. your Harbor), then deploy it in namespace `fathom-ai`. A Deployment and ClusterIP Service will be created in the next validated stage.
