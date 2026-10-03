# Troubleshooting Evidence — ImagePullBackOff

> Estado: **pendiente de ejecución**.

Este archivo se completa después de ejecutar el laboratorio. No incluir outputs inventados.

## Symptom

Describir qué se observa inicialmente.

## Initial state

### Command

```bash
kubectl get pods
```

### Output

```text
PENDIENTE
```

## Investigation

### Pod details

```bash
kubectl describe pod nginx-lab
```

Salida relevante:

```text
PENDIENTE
```

### Events

```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

Salida relevante:

```text
PENDIENTE
```

### Logs

```bash
kubectl logs nginx-lab
```

Resultado y explicación:

```text
PENDIENTE
```

## Hypothesis

PENDIENTE.

## Evidence supporting or rejecting the hypothesis

PENDIENTE.

## Root cause

PENDIENTE.

## Fix

PENDIENTE.

## Verification

### Pod state after fix

```bash
kubectl get pod nginx-lab
```

```text
PENDIENTE
```

### HTTP verification

```bash
kubectl port-forward pod/nginx-lab 8080:80
curl http://localhost:8080
```

```text
PENDIENTE
```

## What happened internally?

PENDIENTE.

Explicar al menos:

- qué componente detectó que necesitaba la imagen;
- qué ocurrió durante el pull;
- por qué aparecieron reintentos;
- por qué el contenedor no produjo logs de aplicación.

## Interview notes

PENDIENTE.
