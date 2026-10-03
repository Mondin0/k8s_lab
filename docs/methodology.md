# Troubleshooting Methodology

Los laboratorios siguen una metodología común para evitar resolver problemas por prueba y error.

## 1. Observar

Identificar el síntoma sin modificar todavía el sistema.

Ejemplos:

```bash
kubectl get pods
kubectl get deployments
kubectl get services
```

## 2. Recopilar evidencia

Buscar datos que expliquen el estado observado.

```bash
kubectl describe <resource>
kubectl logs <pod>
kubectl get events --sort-by=.metadata.creationTimestamp
```

Según el incidente también se inspeccionan:

- ReplicaSets;
- endpoints;
- DNS;
- requests y limits;
- permisos RBAC;
- mounts;
- métricas;
- logs de aplicación.

## 3. Formular una hipótesis

Escribir una explicación falsable.

Ejemplo:

> El Pod no inicia porque el kubelet no puede descargar la imagen indicada.

## 4. Validar

Buscar una evidencia concreta que confirme o contradiga la hipótesis.

## 5. Corregir

Aplicar el cambio mínimo necesario.

## 6. Verificar

No alcanza con aplicar el cambio.

Se debe comprobar el estado final con evidencia nueva.

## 7. Explicar

El lab termina cuando se puede explicar:

- síntoma;
- causa raíz;
- componente involucrado;
- evidencia utilizada;
- corrección;
- validación posterior.

## Principio

```text
symptom != root cause
```

El objetivo es desarrollar criterio operativo, no solamente encontrar el comando que hace desaparecer el error.
