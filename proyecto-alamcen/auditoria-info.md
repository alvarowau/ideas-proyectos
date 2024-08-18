# Microservicio de Auditoría

## Descripción
El microservicio de Auditoría se encarga de registrar y gestionar los logs de acciones realizadas en el sistema. Este servicio permite el seguimiento de las actividades realizadas por los usuarios y sistemas, proporcionando una capa adicional de seguridad y trazabilidad.

### Clases `enum`
- **ActionType**: Enum para representar el tipo de acción auditada.
  - **USER_LOGIN**: Inicio de sesión de un usuario.
  - **USER_LOGOUT**: Cierre de sesión de un usuario.
  - **CREATE**: Creación de una entidad (e.g., pedido, producto).
  - **UPDATE**: Actualización de una entidad.
  - **DELETE**: Eliminación de una entidad.
  - **ACCESS**: Acceso a una entidad o recurso.

### Persistencia en la Base de Datos
- **AuditLog**: Registro de auditoría de acciones realizadas en el sistema.
  - `logId`: Identificador único del registro de auditoría.
  - `user`: Usuario que realizó la acción (referencia al `User`).
  - `actionType`: Tipo de acción realizada (`USER_LOGIN`, `CREATE`, `UPDATE`, etc.).
  - `timestamp`: Fecha y hora en que se realizó la acción.
  - `details`: Detalles adicionales sobre la acción realizada.
  - `entityId`: Identificador de la entidad afectada (opcional).
  - `entityType`: Tipo de entidad afectada (opcional).

### Clases Relacionadas
- **User**: Clase que representa a un usuario del sistema. Contiene:
  - `userId`: Identificador único del usuario.

### Endpoints

#### Registro de Acción de Auditoría
- **Método**: POST
- **Ruta**: `/audit/logs`
- **Descripción**: Registra un nuevo evento de auditoría.
- **Request Body**: Datos del evento de auditoría, incluyendo `user`, `actionType`, `timestamp`, `details`, `entityId`, y `entityType`.
- **Response**: Confirmación del registro del evento de auditoría.

#### Consulta de Logs de Auditoría
- **Método**: GET
- **Ruta**: `/audit/logs`
- **Descripción**: Recupera los registros de auditoría en función de los filtros aplicados.
- **Query Parameters**: 
  - `userId` (opcional): Filtrar por el identificador del usuario.
  - `actionType` (opcional): Filtrar por el tipo de acción.
  - `dateFrom` (opcional): Filtrar por fecha desde.
  - `dateTo` (opcional): Filtrar por fecha hasta.
- **Response**: Lista de registros de auditoría que coinciden con los filtros aplicados.

#### Eliminación de Logs de Auditoría
- **Método**: DELETE
- **Ruta**: `/audit/logs/{logId}`
- **Descripción**: Permite eliminar un registro de auditoría específico.
- **Response**: Confirmación de la eliminación del registro.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Los registros de auditoría pueden crecer rápidamente, y NoSQL ofrece la escalabilidad necesaria para manejar grandes volúmenes de datos, así como la flexibilidad para adaptarse a diferentes tipos de acciones y entidades.

### Integraciones
- **Microservicio de Usuarios**: Para registrar acciones relacionadas con los usuarios, como inicios de sesión y actualizaciones de perfil.
- **Microservicio de Gestión de Pedidos**: Para auditar las acciones realizadas sobre pedidos.
- **Microservicio de Gestión de Productos**: Para auditar las acciones realizadas sobre productos y sus atributos.

### Consideraciones Adicionales
- **Retención de Datos**: Implementar políticas de retención de registros para cumplir con las normativas y evitar el almacenamiento innecesario de logs antiguos.
- **Seguridad**: Asegurar que los registros de auditoría sean inmutables y solo accesibles para usuarios autorizados, protegiendo la integridad y confidencialidad de la información.
- **Análisis de Auditoría**: Considerar la integración de herramientas de análisis para identificar patrones y posibles anomalías en los registros de auditoría.

