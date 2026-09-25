# AGENTS.md — k8s_lab

Entorno estándar: `kind` cluster `k8s-lab` (`kind create cluster --name k8s-lab`).
Idioma: español rioplatense, directo, sin rodeos.

Estructura: `01-core` → `02-scheduling` → `03-storage` → `04-networking` → `05-rbac` → `06-helm` → `07-argocd` → `08-observability`. Cada lab tiene `README.md` + `manifests/`.

Reglas operativas:
- No escribir YAML de memoria. Generar con `kubectl run/create --dry-run=client -o yaml` y consultar con `kubectl explain`.
- Metodología por lab: observar → evidencia (`describe/logs/events`) → hipótesis → validar → corregir → verificar.
- Validar con outputs reales de `kubectl`, no con "creo que anda".
- Para dudas de labs invocar a `@k8s-maestro`.
