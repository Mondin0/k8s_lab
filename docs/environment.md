# Environment

## Cluster local

Los laboratorios utilizan un cluster local de Kubernetes creado con `kind`.

```bash
kind create cluster --name k8s-lab
```

Verificar:

```bash
kubectl cluster-info --context kind-k8s-lab
kubectl get nodes -o wide
```

## Herramientas

- Docker
- kind
- kubectl

Según el bloque de entrenamiento también pueden incorporarse:

- Helm
- ArgoCD
- Prometheus
- Grafana
- Loki

## Reinicio limpio

Cuando un escenario requiere reconstruir completamente el entorno:

```bash
kind delete cluster --name k8s-lab
kind create cluster --name k8s-lab
```

Los labs deben indicar cualquier requisito adicional.
