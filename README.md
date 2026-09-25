# Kubernetes Labs

Repositorio personal de práctica orientado a administración, operación y troubleshooting de Kubernetes.

El objetivo no es memorizar manifests, sino desarrollar criterio operativo para trabajar con clusters reales: desplegar workloads, diagnosticar fallas, entender scheduling, networking, storage, seguridad y automatización.

## Objetivos

- Fortalecer fundamentos de Kubernetes.
- Practicar troubleshooting sobre escenarios reales.
- Mejorar el uso de `kubectl`.
- Entender el comportamiento interno del cluster.
- Trabajar con manifests, Helm y GitOps.
- Preparar conocimientos aplicables a roles DevOps/SRE.

## Estructura

```text
.
├── 01-core
├── 02-scheduling
├── 03-storage
├── 04-networking
├── 05-rbac
├── 06-helm
├── 07-argocd
└── 08-observability
```

### 01-core

Fundamentos de workloads y objetos básicos:

- Pods
- Deployments
- Services
- ConfigMaps
- Secrets
- Probes
- Resources

### 02-scheduling

Control de ubicación y recursos:

- Requests y limits
- Node selectors
- Taints y tolerations
- Affinity y anti-affinity
- Scheduling failures

### 03-storage

Persistencia:

- Volumes
- PersistentVolumes
- PersistentVolumeClaims
- StorageClasses
- Stateful workloads

### 04-networking

Comunicación dentro y fuera del cluster:

- Services
- DNS
- Ingress
- NetworkPolicies
- Debug de conectividad

### 05-rbac

Seguridad y permisos:

- ServiceAccounts
- Roles
- ClusterRoles
- RoleBindings
- ClusterRoleBindings

### 06-helm

Packaging y reutilización:

- Charts
- Templates
- Values
- Releases
- Upgrades
- Rollbacks

### 07-argocd

GitOps:

- Applications
- Sync
- Drift
- Rollbacks
- Declarative deployments

### 08-observability

Observabilidad y operación:

- Metrics
- Logs
- Prometheus
- Grafana
- Loki
- Troubleshooting

## Metodología

Cada laboratorio intenta reproducir un problema o escenario concreto.

La estructura general es:

```text
lab/
├── README.md
└── manifests/
```

Cada `README.md` contiene:

- escenario;
- requisitos;
- problema a resolver;
- comandos útiles;
- criterios de validación;
- notas de troubleshooting.

## Reglas de práctica

- Usar herramientas reales de trabajo.
- No depender de escribir YAML completamente de memoria.
- Usar `kubectl explain`, documentación y generación de manifests cuando sea necesario.
- Antes de corregir un error, entender la causa.
- Documentar la evidencia encontrada.
- Romper cosas intencionalmente.
- Intentar resolver el problema antes de buscar la solución.

## Comandos frecuentes

```bash
kubectl get pods
kubectl get pods -o wide
kubectl describe pod <pod>
kubectl logs <pod>
kubectl get events
kubectl explain <resource>
```

## Progreso

- [ ] Core
- [ ] Scheduling
- [ ] Storage
- [ ] Networking
- [ ] RBAC
- [ ] Helm
- [ ] ArgoCD
- [ ] Observability

## Meta

Poder recibir un cluster o workload con problemas y seguir un proceso sistemático:

```text
observar
   ↓
recopilar evidencia
   ↓
formular hipótesis
   ↓
validar
   ↓
corregir
   ↓
verificar
```

El objetivo final es desarrollar autonomía operativa sobre Kubernetes, no solamente conocer su sintaxis.