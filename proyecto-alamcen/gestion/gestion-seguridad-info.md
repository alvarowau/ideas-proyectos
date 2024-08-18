## Microservicio de Seguridad

### Descripción
El Microservicio de Seguridad se encarga de gestionar los aspectos relacionados con la seguridad en la aplicación, como la autenticación de usuarios, autorización, y manejo de roles y permisos. Proporciona servicios reutilizables que pueden ser invocados por otros microservicios para asegurar un acceso seguro y controlado.

### Clases `enum`
- **Role**: Enum que representa los diferentes roles que pueden existir en el sistema.
  - **ADMIN**: Acceso total a todas las funcionalidades del sistema.
  - **SELLER**: Acceso a funcionalidades relacionadas con la gestión de productos y pedidos.
  - **BUYER**: Acceso a funcionalidades de compra y gestión de cuentas personales.

- **Permission**: Enum para representar permisos específicos dentro del sistema.
  - **READ**: Permiso de lectura de datos.
  - **WRITE**: Permiso de escritura o modificación de datos.
  - **DELETE**: Permiso para eliminar datos.

### Persistencia en la Base de Datos
- **UserCredentials**: Clase que representa las credenciales de los usuarios.
  - `userId`: Identificador único del usuario.
  - `username`: Nombre de usuario.
  - `password`: Contraseña encriptada.
  - `roles`: Lista de roles asignados al usuario.

- **RoleAssignment**: Clase que representa la asignación de roles a usuarios.
  - `roleId`: Identificador único del rol.
  - `roleName`: Nombre del rol (`ADMIN`, `SELLER`, `BUYER`).
  - `permissions`: Lista de permisos asociados con el rol.

### Endpoints

#### Autenticación de Usuario
- **Método**: POST
- **Ruta**: `/auth/login`
- **Descripción**: Autentica a un usuario con su nombre de usuario y contraseña.
- **Request Body**:
  - `username`: Nombre de usuario.
  - `password`: Contraseña del usuario.
- **Response**: Token de autenticación si las credenciales son válidas.

#### Verificar Token de Autenticación
- **Método**: POST
- **Ruta**: `/auth/verify`
- **Descripción**: Verifica la validez de un token de autenticación.
- **Request Body**:
  - `token`: Token de autenticación.
- **Response**: Detalles del usuario autenticado si el token es válido.

#### Asignar Rol a Usuario
- **Método**: POST
- **Ruta**: `/roles/assign`
- **Descripción**: Asigna un rol específico a un usuario.
- **Request Body**:
  - `userId`: Identificador del usuario.
  - `roleId`: Identificador del rol a asignar.
- **Response**: Confirmación de la asignación del rol.

#### Revocar Rol de Usuario
- **Método**: DELETE
- **Ruta**: `/roles/revoke`
- **Descripción**: Revoca un rol asignado a un usuario.
- **Request Body**:
  - `userId`: Identificador del usuario.
  - `roleId`: Identificador del rol a revocar.
- **Response**: Confirmación de la revocación del rol.

#### Obtener Roles de un Usuario
- **Método**: GET
- **Ruta**: `/roles/{userId}`
- **Descripción**: Recupera la lista de roles asignados a un usuario específico.
- **Response**: Lista de roles asociados con el usuario.

