# Proyecto Docente — Diseño

**Fecha:** 2026-04-30
**Alcance:** Gestión de novedades docentes para un cuatrimestre, desde la carga por el Jefe de Cátedra hasta la generación del Excel y aprobación final.

---

## Contexto y Limitaciones

- Se realiza antes del inicio de cada cuatrimestre (2 por año).
- Cada docente puede tener un único tipo de cambio (alta, baja, o cambio de dedicación/cargo) en una sola cátedra, aunque trabaje en varias.
- Un Proyecto Docente puede contener novedades de los tres tipos simultáneamente.
- Los docentes sin novedades no requieren ninguna acción; se incluyen automáticamente en el Excel final con sus datos previos.
- Existen materias compartidas entre carreras con distintos códigos internos; un solo Coordinador es el responsable de aprobarlas.
- La Secretaría Académica Universitaria es un actor externo al sistema; su intervención se registra manualmente por el Decanato o la Secretaría Académica del Departamento.

---

## Estados del Proyecto Docente

```
Borrador → Enviado → En revisión (Coordinador) → Aprobado por Coordinador
→ Aprobado por Secretaría Académica Depto. → Aprobado por Decanato
→ Pendiente (esperando respuesta de Sec. Académica Universitaria)
→ Aprobado/Finalizado
```

Estados adicionales posibles en puntos intermedios:

- **Rechazado** — devuelto al Jefe de Cátedra con justificativo.
- **Objetado** — devuelto al Decanato tras registrar objeciones de la Sec. Académica Universitaria.

Cada novedad individual tiene su propio sub-estado: `pendiente`, `aprobada`, `rechazada`, `modificada`, `objetada`.

---

## Perfiles y Flujos

### Jefe de Cátedra

- Crea el Proyecto Docente cargando únicamente las novedades de su cátedra.
- Por cada docente con novedad, especifica el tipo de cambio (alta, baja, o cambio de dedicación/cargo).
- Al enviar, el proyecto queda disponible para el Coordinador de cada carrera involucrada.
- Si una novedad es rechazada, recibe notificación por sistema y email para corregir o tomar nota.

### Coordinador de Carrera

- Ve las novedades docente por docente dentro de su carrera.
- Por cada novedad puede:
  - **Rechazar** (error de carga o denegación del cambio): la novedad vuelve al Jefe de Cátedra con justificativo. Notificación por sistema y email al Jefe.
  - **Modificar** (ajuste dentro de su autoridad): edita la novedad con justificativo. Notificación por sistema y email al docente y al Jefe de Cátedra.
  - **Aprobar**: la novedad avanza a la Secretaría Académica del Departamento.
- Puede ordenar las novedades por prioridad con una observación justificada.
- Vista detallada por docente incluye:
  - Cátedras en las que participa, con cargo y dedicación en cada una.
  - Historial de novedades previas.
  - Horas de investigación.
  - Indicador si el docente tiene horas en otro Departamento (fuera de Ingeniería).
  - Jefe de Cátedra que envió la novedad y desde qué cátedra.

**Materias compartidas:** cuando una materia pertenece a varias carreras, un único Coordinador es el responsable de aprobarla. Esa asignación se coordina entre los Coordinadores involucrados fuera del sistema y debe estar configurada en el sistema antes de que comience el proceso. Las novedades de esa materia solo aparecen en la vista del Coordinador asignado.

### Secretaría Académica del Departamento de Ingeniería

- Mismas opciones que el Coordinador (rechazar, modificar, aprobar).
- Visibilidad sobre todas las novedades del departamento, no solo una carrera.
- Vista combinada: resumen consolidado por defecto, con posibilidad de bajar al detalle docente por docente.
- Al aprobar, la novedad avanza al Decanato.

### Decanato

- Vista combinada: resumen consolidado por defecto, con posibilidad de bajar al detalle docente por docente.
- Mismas opciones de rechazar, modificar y aprobar que la Secretaría Académica del Departamento.
- Puede cargar novedades de Docentes Especiales directamente.
- Al dar la aprobación, el proyecto pasa a estado **Pendiente** → habilita la generación del Excel.
- Cuando la Secretaría Académica Universitaria responde (fuera del sistema), el Decanato o la Secretaría del Departamento:
  - Registran la **aprobación final** en el sistema.
  - O registran las **novedades objetadas** → cada una vuelve al flujo de corrección desde el Decanato hacia abajo.

---

## Notificaciones

| Evento                                                   | Destinatarios                      |
| -------------------------------------------------------- | ---------------------------------- |
| Novedad rechazada                                        | Jefe de Cátedra que la envió       |
| Novedad modificada por Coordinador                       | Jefe de Cátedra + docente afectado |
| Novedades objetadas registradas por Decanato/Sec. Depto. | Jefe de Cátedra correspondiente    |

Canal: sistema interno + email.

---

## Generación del Excel

- Habilitada únicamente después de que el Decanato de la aprobacion.
- Incluye todas las novedades aprobadas más los docentes sin novedades con sus datos previos.
- Destinado a presentar ante la Secretaría Académica Universitaria.

---

## Fuera de Alcance (Pendiente de Investigación)

- **Segunda instancia de reclamos:** existe una instancia post-aprobación donde se pueden presentar reclamos sobre las novedades finales. El flujo exacto está pendiente de investigación antes de diseñar.
