# Pantallas — Proyecto Docente

**Fecha:** 2026-04-30
**Alcance:** Mapa de pantallas y estructura de navegación para el flujo completo del Proyecto Docente, desde la carga por el Jefe de Cátedra hasta el cierre por el Decanato.

---

## Decisiones de Arquitectura de UI

- **Plataforma:** Web app, desktop-first.
- **Enfoque de navegación:** Híbrido — dashboards y entrypoints separados por rol; pantallas de detalle reutilizadas con acciones contextuales.
- **Layout base:** Topbar fijo (logo + rol activo + notificaciones + usuario) + sidebar izquierdo (secciones del rol activo) + área de contenido principal. El sidebar varía según el rol logueado.
- **Colores:** Background (#ffffff) y Color Primario (#0f9977).

---

## Pantalla Compartida

**Detalle de Docente** (pantallas 12, 16 y 20) es una única pantalla reutilizada por Coordinador, Secretaría Académica y Decanato. Muestra:

- Cátedras en las que participa el docente, con cargo y dedicación en cada una.
- Jefe de Cátedra que envió la novedad y desde qué cátedra.
- Historial de novedades previas.
- Horas de investigación.
- Indicador si el docente tiene horas en otro Departamento (fuera de Ingeniería).

El panel de acciones (aprobar / rechazar / modificar + justificativo) varía según el rol:

| Rol                  | Acciones disponibles                    |
| -------------------- | --------------------------------------- |
| Coordinador          | Aprobar, Rechazar, Modificar, Priorizar |
| Secretaría Académica | Aprobar, Rechazar, Modificar            |
| Decanato             | Aprobar, Rechazar, Modificar            |

---

## Inventario de Pantallas

### Autenticación

| #   | Pantalla                 | Descripción                                                                   |
| --- | ------------------------ | ----------------------------------------------------------------------------- |
| 01  | Login                    | Acceso al sistema.                                                            |
| 02  | Centro de Notificaciones | Panel global de notificaciones accesible desde el topbar por todos los roles. |

---

### Docente

| #   | Pantalla                         | Descripción                                                                                                                            |
| --- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| 03  | Dashboard — Estado de mi Novedad | Vista principal del docente. Muestra el estado actual de su novedad en el ciclo de aprobación y el historial de cambios. Solo lectura. |
| 04  | Mi Perfil Docente                | _(WIP — fuera de alcance de este diseño)_                                                                                              |
| 05  | Reserva de Aula / Laboratorio    | _(WIP — fuera de alcance de este diseño)_                                                                                              |

---

### Jefe de Cátedra

| #   | Pantalla                           | Descripción                                                                                                                                                 |
| --- | ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 06  | Dashboard — Mis Proyectos Docentes | Lista de proyectos docentes creados por el Jefe de Cátedra. Muestra estado de cada proyecto (borrador, enviado, en revisión, aprobado, rechazado).          |
| 07  | Crear / Editar Proyecto Docente    | Formulario para crear o editar un Proyecto Docente. Lista los docentes de la cátedra e indica cuáles tienen novedades cargadas.                             |
| 08  | Detalle del Proyecto Docente       | Vista de seguimiento del proyecto: estado actual, timeline de aprobación, listado de novedades con su sub-estado individual, y feedback en caso de rechazo. |
| 09  | Formulario de Novedad              | Carga o edición de una novedad individual (alta, baja o cambio de dedicación/cargo). Un docente solo puede tener un tipo de cambio por proyecto.            |

---

### Coordinador de Carrera

| #   | Pantalla                            | Descripción                                                                                                               |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| 10  | Dashboard — Novedades de mi Carrera | Resumen de las novedades recibidas en la carrera asignada: pendientes de revisión, aprobadas, rechazadas.                 |
| 11  | Lista de Novedades                  | Lista filtrable de novedades de la carrera (por estado, tipo de cambio, cátedra). Punto de entrada al Detalle de Docente. |
| 12  | Detalle de Docente _(compartida)_   | Ver descripción en sección "Pantalla Compartida". Acciones disponibles: Aprobar, Rechazar, Modificar, Priorizar.          |
| 13  | Priorización de Novedades           | Permite ordenar las novedades de la carrera por prioridad con una observación justificada.                                |

> **Materias compartidas:** cuando una materia pertenece a varias carreras, solo aparece en la vista del Coordinador asignado como responsable. Esa asignación se configura en Administración antes de iniciar el proceso.

---

### Secretaría Académica del Departamento

| #   | Pantalla                                 | Descripción                                                                                                                                         |
| --- | ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 14  | Dashboard — Consolidado del Departamento | Resumen de todas las novedades del departamento agrupadas por estado.                                                                               |
| 15  | Vista Consolidada de Novedades           | Lista completa del departamento, filtrable por carrera, tipo de cambio y estado. Vista por defecto consolidada con posibilidad de bajar al detalle. |
| 16  | Detalle de Docente _(compartida)_        | Ver descripción en sección "Pantalla Compartida". Acciones disponibles: Aprobar, Rechazar, Modificar.                                               |
| 17  | Configuración de Materias Compartidas    | Asignación de qué Coordinador es responsable de aprobar cada materia compartida entre carreras.                                                     |

---

### Decanato

| #   | Pantalla                                 | Descripción                                                                                                                                                                                              |
| --- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 18  | Dashboard — Consolidado General          | Resumen de todas las novedades del departamento con estado del ciclo global del Proyecto Docente.                                                                                                        |
| 19  | Vista Consolidada de Novedades           | Lista completa del departamento, filtrable por carrera, tipo de cambio y estado. Incluye indicador del estado global del ciclo. Al aprobar todas las novedades, habilita la pantalla 22 (Generar Excel). |
| 20  | Detalle de Docente _(compartida)_        | Ver descripción en sección "Pantalla Compartida". Acciones disponibles: Aprobar, Rechazar, Modificar.                                                                                                    |
| 21  | Carga de Novedades — Docentes Especiales | Formulario de carga directa de novedades de Docentes Especiales, sin pasar por el flujo del Jefe de Cátedra.                                                                                             |
| 22  | Generar Excel                            | Habilitada únicamente después de la aprobación del Decanato. Genera el Excel con todas las novedades aprobadas más los docentes sin novedades con sus datos previos.                                     |
| 23  | Registrar Aprobación Final / Objeciones  | Permite registrar manualmente la respuesta de la Secretaría Académica Universitaria: aprobación final o listado de novedades objetadas. Las objeciones reingresan al flujo de corrección.                |

---

### Administrador

| #   | Pantalla                              | Descripción                                                                  |
| --- | ------------------------------------- | ---------------------------------------------------------------------------- |
| 24  | Gestión de Usuarios y Roles           | ABM de usuarios del sistema y asignación de roles.                           |
| 25  | Configuración de Materias Compartidas | Misma función que pantalla 17. Accesible también desde el rol Administrador. |
| 26  | Configuración del Sistema             | Gestión de cuatrimestres, carreras, cátedras y otros parámetros del sistema. |

---

## Flujo entre Pantallas

```
[Jefe de Cátedra]
06 Mis Proyectos → 07 Crear Proyecto → 09 Formulario Novedad → 08 Detalle Proyecto
                                                                      ↓ Envía
[Coordinador]
10 Dashboard → 11 Lista Novedades → 12 Detalle Docente → Aprobar / Rechazar / Modificar
                                    13 Priorización (opcional)
                                         ↓ Si rechaza → notificación al JC (08)
                                         ↓ Si aprueba →

[Secretaría Académica]
14 Dashboard → 15 Vista Consolidada → 16 Detalle Docente → Aprobar / Rechazar / Modificar
                                          ↓ Si aprueba →

[Decanato]
18 Dashboard → 19 Vista Consolidada → 20 Detalle Docente → Aprobar → habilita 22 Generar Excel
21 Carga Doc. Especiales (flujo paralelo, carga directa)
23 Aprobación Final / Objeciones → si hay objeciones, vuelven al flujo desde Decanato

[Docente]
03 Estado de mi Novedad → solo lectura, actualizado en tiempo real
```

---

## Fuera de Alcance

- Segunda instancia de reclamos post-aprobación (pendiente de investigación).
- Perfil Docente completo (WIP).
- Reserva de Aula / Laboratorio (WIP).
