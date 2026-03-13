# Anexos - Introducción al Diseño Orientado a Objetos
## Los cuatro fundamentos de POO
## Requisitos iniciales del sistema
## Casos de uso
### - Agendar Turno

**Nombre del caso de uso:** Agendar Turno.

**Actor(es) involucrado(s):** Secretaria.

**Descripción breve:** Permite a la secretaria asignar una cita a un paciente con un profesional específico, validando que el horario esté libre y que se cumplan las reglas de negocio (duración según tipo de consulta y restricciones horarias del médico).

**Flujo principal de eventos:**

* La secretaria selecciona la opción "Nuevo Turno" desde la vista de la agenda.

* El sistema solicita los datos del paciente (búsqueda por DNI o Nombre).

* La secretaria selecciona al Profesional y el Tipo de Consulta (Control o Primera Consulta).

* El sistema muestra un calendario con los huecos disponibles, filtrando automáticamente las restricciones (ej: bloquea los jueves por la tarde y no muestra "Primeras Consultas" los viernes a última hora).

* La secretaria selecciona una fecha y una hora de la lista de espacios disponibles (15 min para control, 30 min para primera consulta).

* La secretaria confirma la reserva del turno.

* El sistema verifica internamente que no haya ocurrido una superposición durante el proceso (validación de concurrencia).

* El sistema registra el turno con estado "Pendiente" y muestra un mensaje de confirmación exitosa.

**Precondiciones:**

* La secretaria debe estar autenticada en el sistema.

* El profesional debe estar registrado con sus horarios de atención base definidos.

* El paciente debe existir en el sistema (o el sistema debe permitir su creación rápida en el flujo).


**Postcondiciones:**

* El turno queda guardado en la base de datos vinculado al paciente y al profesional.

* El horario seleccionado queda marcado como "Ocupado" en la agenda, impidiendo nuevas reservas en ese bloque.

* Se genera de forma automática una tarea programada para el envío del recordatorio (WhatsApp/Email) el día anterior a la cita.


Registrar Llegada de Paciente

Gestionar Disponibilidad

Reprogramar Turno

Consultar Agenda


## Boceto inicial de diseño de clases
