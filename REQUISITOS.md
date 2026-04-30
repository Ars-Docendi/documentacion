# Gestion Docente - Requisitos Funcionales

## Proyecto Docente

### Limitaciones:

- Se realiza antes del inicio de un nuevo cuatrimestre (hay 2 cuatrimestres por año).
- Los docentes solo pueden tener cambios en una sola materia.
- Los docentes sin novedades deben incluir los datos previos sin cambio alguno.
- Existen materias compartidas entre varias carreras (pero con distintos codigos internos en cada una), un solo coordinador debe aprobarlas, usualmente lo gestionan entre ellos.
- Luego de la aprobacion del Decanato el "proyecto docente" queda en estado pendiente hasta recibir la aprobacion final de la Secretaria Academica Universitaria, de ahi pueden darlo como aprobado/finalizado (solamente el Decanato o la Secretaria Academica del Departamento).
- La Secretaria Academica Universitaria puede objetar algunas novedades antes de enviar la aprobacion final [TODO: Terminar de investigar ese flujo].
- Luego de la aprobacion final existe una segunda instancia donde se pueden realizar reclamos sobre las novedades finales [TODO: Terminar de investigar ese flujo].

### Perfiles:

#### Jefe de Catedra:

- Genera el "proyecto docente" para su Catedra con las novedades de sus docentes (incluyendo las suyas).
- Hay tres tipos de cambios, solo se permite una de ellas por proyecto; alta, baja y cambios en la dedicacion y/o cargo.

#### Coordinadores de Carreras:

- Recibe las novedades enviadas en el "proyecto docente" de cada Jefe de Catedra (dentro de su carrera asignada como coordinador).
- Cada novedad esta vinculada a un docente, el Coordinador puede aprobar o rechazar esa novedad, esa novedad debe detallar que Jefe de Catedra lo envio (y desde que Catedra).
- Su vista es enfocada en docente por docente y no tanto en la catedra, pero por cada docente deberia detallar en que catedras esta; cargo y dedicacion en cada una; historial de novedades previas y horas de investigacion.
- Se debe indicar si un docente hace mas horas en otro Departamento (que no sea el de Ingenieria).
- Debatiendo dos flujos de cambios en las novedades: [TODO: Definir cual de los dos flujos implementar]
  1. Puede rechazar por un dato mal cargado o denegar los cambios del docente, todo con un justificativo. Esto luego se reenvia al Jefe de Catedra que envio esa novedad para correcion o aviso (notificacion mediante el sistema y por email).
  2. O, en lugar de rechazarlo puede hacer modificaciones en las novedades del docente, con sus justificativos. Notificando al docente (y Jefe de Catedra que envio esa novedad) por el sistema y por email.
- Puede ordenar las novedades de cada docente por prioridad, con una observacion justificando la importancia (o no) de este cambio. Contexto, algunas novedades son necesarias para evitar que una Catedra se quede sin docentes.
- Al aprobar una novedad esta se envia a la Secretaria Academica del Departamento de Ingenieria.

#### Secretaria Academica del Departamento de Ingenieria:

- Mismas opciones que el Coordinador, pero pueden ver las novedades de todo el departamento y no solo una Carrera.
- Al aprobar una novedad esta se envia al Decanato.

#### Decanato:

- Mismas opciones que la Secretaria Academica del Departamento de Ingenieria.
- Puede cargar novedades de Docentes Especiales.
- Aprobacion final, habilita la generacion del Excel para presentar a la Secretaria Academica.
- [TODO: ¿Deberia resumirse las novedades para su aprobacion o debe seguir el mismo flujo que los coordinadores y Secretaria Academica, es decir, ir docente por docente?]

## Reserva de aulas / laboratorios (para examenes)

## Seguimiento de Tareas

## Chatbot de consultas

https://github.com/defog-ai/sqlcoder

## Integridad de las transacciones (blockchain)
