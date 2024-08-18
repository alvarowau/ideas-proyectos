# Microservicio de Gestión de Notificaciones

## Descripción
El microservicio de Gestión de Notificaciones se encarga de enviar y gestionar notificaciones para los usuarios del sistema. Esto incluye la creación de notificaciones, la consulta de notificaciones pendientes y el registro del estado de lectura de las mismas.

### Clases `enum`
- **NotificationType**: Enum para representar el tipo de notificación.
  - **ORDER_UPDATE**: Actualización del estado de un pedido.
  - **PROMOTION**: Notificación sobre una nueva promoción o descuento.
  - **SYSTEM_ALERT**: Alerta del sistema (e.g., mantenimiento programado).

### Persistencia en la Base de Datos
- **Notification**: Información sobre una notificación.
  - `notificationId`: Identificador único de la notificación.
  - `recipient`: Usuario que recibirá la notificación (referencia al `User`).
  - `message`: Contenido del mensaje de la notificación.
  - `timestamp`: Fecha y hora en que se creó la notificación.
  - `read`: Estado indicando si la notificación ha sido leída (`true` o `false`).
  - `type`: Tipo de notificación (`ORDER_UPDATE`, `PROMOTION`, `SYSTEM_ALERT`).

### Clases Relacionadas
- **User**: Clase que representa a un usuario del sistema. Contiene:
  - `userId`: Identificador único del usuario.

### Endpoints

#### Creación de Notificación
- **Método**: POST
- **Ruta**: `/notifications`
- **Descripción**: Permite crear una nueva notificación.
- **Request Body**: Datos de la notificación, incluyendo `recipient`, `message`, `timestamp`, `read`, y `type`.
- **Response**: Confirmación de la creación de la notificación y detalles de la notificación creada.

#### Consulta de Notificaciones Pendientes
- **Método**: GET
- **Ruta**: `/users/{userId}/notifications`
- **Descripción**: Recupera todas las notificaciones pendientes para un usuario específico.
- **Response**: Lista de notificaciones pendientes para el usuario, incluyendo `message`, `timestamp`, `type`, y `read`.

#### Marcar Notificación como Leída
- **Método**: PUT
- **Ruta**: `/notifications/{notificationId}/read`
- **Descripción**: Permite marcar una notificación como leída.
- **Request Body**: Datos para actualizar el estado de lectura (`read`).
- **Response**: Confirmación de la actualización del estado de la notificación.

#### Eliminación de Notificación
- **Método**: DELETE
- **Ruta**: `/notifications/{notificationId}`
- **Descripción**: Permite eliminar una notificación específica.
- **Response**: Confirmación de la eliminación de la notificación.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Las notificaciones son entidades de alto volumen con un formato flexible, y NoSQL proporciona la escalabilidad y la capacidad de manejar grandes volúmenes de datos con frecuencia de escritura alta.

### Integraciones
- **Microservicio de Pedidos**: Para enviar notificaciones sobre el estado de los pedidos.
- **Microservicio de Promociones**: Para notificar a los usuarios sobre nuevas promociones y descuentos.
- **Microservicio de Usuarios**: Para obtener detalles sobre los usuarios que deben recibir las notificaciones.

### Consideraciones Adicionales
- **Escalabilidad**: Considerar la carga de trabajo y el volumen de notificaciones para asegurar que el servicio pueda manejar altos volúmenes de datos y solicitudes.
- **Seguridad**: Asegurar que la información de las notificaciones sea accesible solo para los usuarios autorizados y proteger los datos sensibles.
- **Entrega en Tiempo Real**: Implementar mecanismos para el envío y la actualización de notificaciones en tiempo real para mejorar la experiencia del usuario.

