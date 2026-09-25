# Lab 01 — Pod básico y troubleshooting

## Escenario

Necesitamos desplegar una instancia simple de Nginx dentro de Kubernetes para validar que el cluster puede ejecutar correctamente un workload básico.

El Pod debe quedar operativo y accesible localmente para hacer una prueba HTTP.

## Requisitos

Crear un Pod que cumpla:

- Nombre: `nginx-lab`
- Imagen: `nginx:1.27`
- Label: `app: nginx`
- Puerto del contenedor: `80`

Podés generar una base con `kubectl` y luego modificar el manifest.

## Validación

Una vez desplegado, verificar:

```bash
kubectl get pods
kubectl get pod nginx-lab -o wide
kubectl describe pod nginx-lab
```

El Pod debe quedar en estado:

```text
Running
```

Luego probar el servicio localmente usando `port-forward`:

```bash
kubectl port-forward pod/nginx-lab 8080:80
```

En otra terminal:

```bash
curl http://localhost:8080
```

La respuesta debe devolver el HTML de Nginx.

---

# Incidente

Una actualización del deployment introduce una imagen incorrecta:

```text
nginx:1.27-invalid
```

Modificar el Pod para utilizar esa imagen y aplicar nuevamente el manifest.

## Objetivo de troubleshooting

Sin corregir inmediatamente el problema, investigar qué está ocurriendo.

Responder:

1. ¿Cuál es el estado del Pod?
2. ¿El contenedor llegó a ejecutarse?
3. ¿Qué muestra `kubectl describe pod`?
4. ¿Qué eventos genera Kubernetes?
5. ¿Qué componente intenta descargar la imagen?
6. ¿Por qué Kubernetes sigue intentando iniciar el contenedor?
7. ¿Qué diferencia hay entre `ErrImagePull` e `ImagePullBackOff`?

## Comandos permitidos

Podés usar cualquier herramienta normal de Kubernetes, por ejemplo:

```bash
kubectl get
kubectl describe
kubectl logs
kubectl get events
kubectl explain
```

No buscar directamente la solución del incidente.

## Criterio de finalización

El laboratorio está terminado cuando:

- el Pod funciona correctamente;
- podés provocar el error de imagen;
- identificás la causa usando información del cluster;
- corregís el problema;
- podés explicar qué ocurrió sin depender únicamente del mensaje de error.

## Notas

Documentar brevemente:

- causa raíz;
- comandos utilizados;
- evidencia encontrada;
- solución aplicada.