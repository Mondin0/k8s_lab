# Kubernetes Operations Lab

Repositorio personal de entrenamiento práctico orientado a **operación, troubleshooting y Platform Engineering con Kubernetes**.

El objetivo no es acumular manifests ni memorizar YAML. Cada laboratorio busca demostrar una capacidad operativa concreta mediante un escenario reproducible, una falla intencional, evidencia obtenida desde el cluster y una explicación de causa raíz.

## Qué demuestra este repositorio

Cada lab sigue este ciclo:

```text
deploy
  ↓
break
  ↓
observe
  ↓
collect evidence
  ↓
form a hypothesis
  ↓
fix
  ↓
verify
  ↓
explain
```

La evidencia importa más que el resultado final: `kubectl describe`, logs, events, endpoints, DNS, métricas y otros datos del cluster deben sostener el diagnóstico.

## Entorno

Entorno base de laboratorio:

- Kubernetes local con `kind`
- cluster: `k8s-lab`
- `kubectl`
- Docker

Ver [docs/environment.md](docs/environment.md).

## Progreso

| Área | Laboratorio | Estado | Evidencia |
| --- | --- | --- | --- |
| Core | Pod + ImagePullBackOff | 🔄 En progreso | [troubleshooting](01-core/01-pod/evidence/troubleshooting.md) |
| Core | Deployment + rollout failure | ⬜ Planificado | — |
| Core | Service + selector mismatch | ⬜ Planificado | — |
| Core | ConfigMap / Secret | ⬜ Planificado | — |
| Core | Readiness / Liveness probes | ⬜ Planificado | — |
| Scheduling | Requests / limits + FailedScheduling | ⬜ Planificado | — |
| Scheduling | Taints / tolerations | ⬜ Planificado | — |
| Scheduling | Affinity / anti-affinity | ⬜ Planificado | — |
| Storage | PV / PVC troubleshooting | ⬜ Planificado | — |
| Networking | Service / endpoints | ⬜ Planificado | — |
| Networking | DNS | ⬜ Planificado | — |
| Networking | Ingress | ⬜ Planificado | — |
| Networking | NetworkPolicy | ⬜ Planificado | — |
| RBAC | ServiceAccount + Forbidden | ⬜ Planificado | — |
| Helm | Install / upgrade / rollback | ⬜ Planificado | — |
| ArgoCD | Sync / drift / reconciliation | ⬜ Planificado | — |
| Observability | Metrics / logs / troubleshooting | ⬜ Planificado | — |

Un laboratorio pasa a **completado** únicamente cuando contiene evidencia real de ejecución y una explicación de la causa raíz.

## Estructura

```text
.
├── docs/
│   ├── environment.md
│   ├── methodology.md
│   └── learning-log.md
├── templates/
│   ├── lab-readme-template.md
│   └── troubleshooting-template.md
├── 01-core/
├── 02-scheduling/
├── 03-storage/
├── 04-networking/
├── 05-rbac/
├── 06-helm/
├── 07-argocd/
└── 08-observability/
```

Cada laboratorio utiliza, cuando corresponde:

```text
lab/
├── README.md
├── manifests/
│   ├── healthy.yaml
│   └── broken.yaml
└── evidence/
    └── troubleshooting.md
```

## Metodología

Antes de corregir una falla:

1. observar el síntoma;
2. recopilar evidencia;
3. formular una hipótesis;
4. validarla;
5. aplicar una corrección;
6. verificar el estado final;
7. explicar qué ocurrió internamente.

Detalles en [docs/methodology.md](docs/methodology.md).

## Reglas de práctica

- No corregir una falla apenas aparece el mensaje de error.
- Priorizar evidencia del cluster sobre intuición.
- Usar `kubectl explain` y documentación en lugar de memorizar manifests.
- Generar YAML base con `kubectl --dry-run=client -o yaml` cuando sea útil.
- Documentar solamente outputs realmente obtenidos.
- Romper escenarios de forma intencional y reproducible.
- Poder explicar el diagnóstico sin depender únicamente del mensaje final de error.

## Objetivo

Llegar a recibir un workload o cluster con problemas y poder seguir un proceso sistemático de diagnóstico hasta encontrar y demostrar la causa raíz.

Este repositorio funciona como registro de ese entrenamiento.
