# Microservicio de Usuarios

## Descripción
El microservicio de Usuarios gestiona la información de los usuarios del sistema, incluyendo la creación, actualización, eliminación, y gestión de roles y permisos.

### Clases `enum`
- **Role**: Enum para representar los diferentes roles de usuario en el sistema. Los roles incluyen:
  - **ADMIN**: Administrador del sistema.
  - **SELLER**: Vendedor.
  - **BUYER**: Comprador.

### Persistencia en la Base de Datos
- **Usuarios**: Información de los usuarios, incluyendo:
  - `userId`: Identificador único para el usuario.
  - `username`: Nombre de usuario.
  - `password`: Contraseña (almacenada de forma segura con hashing).
  - `email`: Dirección de correo electrónico.
  - `fullName`: Nombre completo del usuario.
  - `role`: Rol del usuario (almacenado como una referencia al `enum Role`).
  - `addressId`: Referencia al identificador de la dirección (relacionado con la clase `Address`).
  - `phoneNumber`: Número de contacto.
- **Órdenes**: Información sobre los pedidos asociados con el usuario (referencia a pedidos en el microservicio de Pedidos).

### Clases Relacionadas
- **Address**: Clase que maneja las direcciones físicas de los usuarios. Contiene:
  - `addressId`: Identificador único para la dirección.
  - `street`: Dirección de la calle.
  - `city`: Ciudad.
  - `state`: Estado o provincia.
  - `postalCode`: Código postal o ZIP.
  - `country`: País.

## Endpoints

### Registro de Usuario
- **Método**: POST
- **Ruta**: `/users/register`
- **Descripción**: Registra un nuevo usuario.
- **Request Body**: Datos del usuario a registrar.
- **Response**: Detalles del usuario creado.

### Autenticación
- **Método**: POST
- **Ruta**: `/users/login`
- **Descripción**: Autentica a un usuario y devuelve un token de sesión.
- **Request Body**: Nombre de usuario y contraseña.
- **Response**: Token de sesión.

### Actualización de Perfil
- **Método**: PUT
- **Ruta**: `/users/{userId}`
- **Descripción**: Actualiza la información del perfil del usuario.
- **Request Body**: Datos actualizados del usuario.
- **Response**: Detalles actualizados del usuario.

### Recuperación de Contraseña
- **Método**: POST
- **Ruta**: `/users/forgot-password`
- **Descripción**: Inicia el proceso de recuperación de contraseña.
- **Request Body**: Correo electrónico del usuario.
- **Response**: Confirmación de solicitud de recuperación.

### Gestión de Roles y Permisos
- **Método**: PUT
- **Ruta**: `/users/{userId}/roles`
- **Descripción**: Actualiza el rol del usuario. Consultar el microservicio de Roles si es necesario.
- **Request Body**: Nuevo rol del usuario.
- **Response**: Detalles actualizados del usuario.

## Base de Datos
- **Elección**: SQL
- **Motivo**: Los datos de usuario son estructurados y requieren integridad y seguridad en la gestión.

## Integraciones
- **Microservicio de Pedidos**: Para consultar la lista de pedidos de un usuario.
- **Microservicio de Productos**: Para gestionar productos que los usuarios gestionan.
- **Microservicio de Notificaciones**: Para enviar notificaciones a los usuarios.
- **Microservicio de Roles**: Para gestionar y consultar roles y permisos.
- **Microservicio de Direcciones**: Para gestionar direcciones asociadas con los usuarios.

## Seguridad
- **Autenticación**: Implementar autenticación mediante tokens JWT.
- **Autorización**: Verificar roles y permisos para acceso a ciertos recursos.

## Consideraciones Adicionales
- **Validación de Datos**: Implementar validaciones para la entrada de datos (por ejemplo, formato de correo electrónico).
- **Registros de Auditoría**: Registrar acciones importantes para auditoría (creación, actualización, eliminación de usuarios).
- **Dirección**: La clase `Address` se maneja como una entidad separada para permitir una gestión consistente de direcciones.
