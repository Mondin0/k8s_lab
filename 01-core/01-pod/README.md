# Lab 01 — Pod + ImagePullBackOff

## Objetivo

Entrenar el ciclo básico de operación y troubleshooting de un Pod:

```text
deploy → verify → break → observe → diagnose → fix → verify
```

El laboratorio utiliza una imagen inválida para reproducir `ErrImagePull` / `ImagePullBackOff`.

## Healthy path

Aplicar:

```bash
kubectl apply -f manifests/pod.yaml
```

Verificar:

```bash
kubectl get pod nginx-lab -o wide
kubectl describe pod nginx-lab
```

El Pod debe alcanzar:

```text
Running
```

Probar HTTP:

```bash
kubectl port-forward pod/nginx-lab 8080:80
```

En otra terminal:

```bash
curl http://localhost:8080
```

## Incident

Eliminar el escenario sano:

```bash
kubectl delete pod nginx-lab
```

Aplicar el manifest roto:

```bash
kubectl apply -f manifests/pod-broken-image.yaml
```

La imagen configurada deliberadamente no existe:

```text
nginx:1.27-invalid
```

## Restricción

No corregir inmediatamente la imagen.

Primero obtener evidencia suficiente para explicar qué está ocurriendo.

## Investigación

Empezar por:

```bash
kubectl get pods
kubectl get pod nginx-lab -o wide
kubectl describe pod nginx-lab
kubectl get events --sort-by=.metadata.creationTimestamp
```

Intentar también:

```bash
kubectl logs nginx-lab
```

Si `logs` no devuelve logs de aplicación, explicar por qué.

## Preguntas a responder

1. ¿Cuál es el estado observado?
2. ¿El contenedor llegó a ejecutarse?
3. ¿Qué evidencia aparece en `describe`?
4. ¿Qué muestran los Events?
5. ¿Qué componente del nodo participa en el image pull?
6. ¿Por qué Kubernetes vuelve a intentarlo?
7. ¿Cuál es la diferencia práctica entre `ErrImagePull` e `ImagePullBackOff`?
8. ¿Por qué `kubectl logs` puede no ser útil en este escenario?

## Evidencia requerida

Completar:

[**evidence/troubleshooting.md**](evidence/troubleshooting.md)

No reemplazar los placeholders con información teórica: deben usarse outputs del cluster ejecutado.

## Fix

Una vez documentado el diagnóstico, volver a utilizar la imagen válida:

```text
nginx:1.27
```

Puede aplicarse nuevamente `manifests/pod.yaml`.

## Criterio de finalización

- [ ] Pod sano desplegado y validado;
- [ ] respuesta HTTP obtenida;
- [ ] incidente reproducido;
- [ ] estado previo al fix documentado;
- [ ] Events inspeccionados;
- [ ] hipótesis escrita;
- [ ] causa raíz respaldada por evidencia;
- [ ] imagen corregida;
- [ ] Pod nuevamente en `Running`;
- [ ] verificación HTTP posterior al fix;
- [ ] explicación interna completada.

## Interview check

Al terminar debería poder explicar, sin mirar el README:

- qué diferencia hay entre un Pod `Pending`, `ErrImagePull` e `ImagePullBackOff`;
- qué información aporta `describe` frente a `logs`;
- quién intenta obtener la imagen;
- por qué existe backoff;
- qué evidencia buscaría primero ante este incidente en producción.
