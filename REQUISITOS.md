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
- Por cada novedad puede:
  1. Rechazar por un dato mal cargado o denegar los cambios del docente, todo con un justificativo. Esto luego se reenvia al Jefe de Catedra que envio esa novedad para correcion o aviso (notificacion mediante el sistema y por email).
  2. O, en lugar de rechazarlo puede hacer modificaciones en las novedades del docente, con sus justificativos. Notificando al docente (y Jefe de Catedra que envio esa novedad) por el sistema y por email.
- Puede ordenar las novedades de cada docente por prioridad, con una observacion justificando la importancia (o no) de este cambio. Contexto, algunas novedades son necesarias para evitar que una Catedra se quede sin docentes.
- Al aprobar una novedad esta se envia a la Secretaria Academica del Departamento de Ingenieria.

#### Secretaria Academica del Departamento de Ingenieria:

- Mismas opciones que el Coordinador, pero pueden ver las novedades de todo el departamento y no solo una Carrera.
- Al aprobar una novedad esta se envia al Decanato.
- Pueden parametrizar los configurables del sistema.
- Puede generar el Excel para presentar a la Secretaria Academica, luego de la aprobacion final por el Decanato.

#### Decanato:

- Mismas opciones que la Secretaria Academica del Departamento de Ingenieria.
- Puede cargar novedades de Docentes Especiales.
- Aprobacion final, habilita la generacion del Excel
- [TODO: ¿Deberia resumirse las novedades para su aprobacion o debe seguir el mismo flujo que los coordinadores y Secretaria Academica, es decir, ir docente por docente?]

#### Administrativos:

- Pueden parametrizar los configurables del sistema.

## Reserva de aulas / laboratorios (para examenes)

- Solicitantes: Docentes o Jefes de Catedra cargan el pedido de aula o laboratorio indicando fecha, materia, capacidad necesaria.
- Gestión Administrativa: El personal administrativo visualiza los pedidos pendientes y gestiona el trámite ante la Secretaría Académica de la universidad o asigna laboratorios propios del departamento.
- Estados del Pedido: Los estados deben incluir: Pendiente, Solicitado, Aula Asignada (indicando el número de aula) o Rechazado.
- Notificaciones: Una vez asignada el aula, el sistema debería disparar un correo electrónico automático al docente solicitante para avisarle (ademas de incluir una notificacion dentro del sistema).

## Portal del Docente

- Actualización de Datos: El docente debe poder modificar sus datos de contacto (teléfono, mail) y cargar sus títulos de grado o posgrado.
- Declaración de Horas: Una función crítica es que el docente declare la distribución de sus horas (cuántas en clase, cuántas en investigación, gestión o posgrado) para que el departamento pueda validar lo que cobra frente a lo que hace.
- Áreas de Experticia: El docente podrá listar sus conocimientos o "skills" para que el departamento sepa a quién contactar si surge una vacante específica.

## Seguimiento de Tareas

- Funcionalidad: Funcionar como un "Trello académico" donde se pueden asignar tareas a uno mismo u otros colaboradores.
- Visualización: Debe incluir un sistema de "semáforo" (verde, amarillo, rojo) para indicar el estado de vencimiento de las tareas.

## Chatbot de consultas

- Chatbot que genera reportes sobre la base de datos en base a las consultas escritas por el usuario.
- Debe ser conciente del rol que tiene el usuario que hace la consulta, no debe mostrar información no disponible para ese rol.
- Open Source model: https://github.com/defog-ai/sqlcoder

# Gestion Docente - Requisitos No Funcionales

- **Integridad de las transacciones (blockchain)**: Comprobación de integridad al estilo blockchain para las transacciones de PostgreSQL. Esto implica crear una cadena de hashs en la que el hash de cada fila depende del hash de la fila anterior, lo que permite detectar cualquier manipulación.
- **Autenticación con las credenciales institucionales de Microsoft**: SSO login con el Active Directory institucional.
- **Web-app responsive**
