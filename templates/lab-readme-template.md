# Lab XX — Título

## Objetivo

¿Qué capacidad operativa entrena este laboratorio?

## Escenario

Describir el sistema antes de la falla.

## Healthy path

### Deploy

```bash
# comandos
```

### Validación

¿Qué evidencia demuestra que el escenario sano funciona?

## Incident

Describir una única falla intencional y reproducible.

## Restricción

No corregir el problema antes de recopilar evidencia.

## Investigación

Comandos posibles:

```bash
kubectl get
kubectl describe
kubectl logs
kubectl get events
kubectl explain
```

Agregar herramientas específicas según el escenario.

## Preguntas a responder

1. ¿Cuál es el síntoma?
2. ¿Cuál es la causa raíz?
3. ¿Qué evidencia la demuestra?
4. ¿Qué componente de Kubernetes está involucrado?
5. ¿Qué cambio corrige el problema?
6. ¿Cómo verifico que quedó resuelto?

## Evidencia

Completar `evidence/troubleshooting.md`.

## Criterio de finalización

- [ ] escenario sano validado;
- [ ] falla reproducida;
- [ ] evidencia recopilada antes del fix;
- [ ] hipótesis documentada;
- [ ] causa raíz identificada;
- [ ] corrección aplicada;
- [ ] estado final verificado;
- [ ] explicación técnica completada.

## Interview check

Preguntas que debería poder responder sin ejecutar comandos.
