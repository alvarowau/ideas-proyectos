# Microservicio de Gestión de Reseñas

## Descripción
El microservicio de Gestión de Reseñas se encarga de manejar las reseñas que los usuarios dejan sobre los productos. Este servicio permite a los usuarios escribir, leer, actualizar y eliminar reseñas para los productos. 

### Clases `enum`
- **Rating**: Enum para representar las calificaciones posibles.
  - **ONE_STAR**: 1 estrella.
  - **TWO_STARS**: 2 estrellas.
  - **THREE_STARS**: 3 estrellas.
  - **FOUR_STARS**: 4 estrellas.
  - **FIVE_STARS**: 5 estrellas.

### Persistencia en la Base de Datos
- **Review**: Información sobre una reseña escrita por un usuario.
  - `reviewId`: Identificador único de la reseña.
  - `productId`: Identificador del producto asociado con la reseña (relacionado con la clase `Product`).
  - `userId`: Identificador del usuario que escribió la reseña (relacionado con la clase `User`).
  - `rating`: Calificación dada a la reseña (almacenado como referencia al `enum Rating`).
  - `comment`: Comentario adicional de la reseña.
  - `reviewDate`: Fecha en que se escribió la reseña.

### Clases Relacionadas
- **Product**: Clase que representa un producto. Contiene:
  - `productId`: Identificador único del producto.
  - `name`: Nombre del producto.
  
- **User**: Clase que representa al usuario. Contiene:
  - `userId`: Identificador único del usuario.
  - `username`: Nombre de usuario.

### Endpoints

#### Creación de Reseña
- **Método**: POST
- **Ruta**: `/reviews`
- **Descripción**: Permite a un usuario crear una nueva reseña para un producto.
- **Request Body**: Datos de la reseña, incluyendo `productId`, `userId`, `rating`, `comment`, y `reviewDate`.
- **Response**: Confirmación de la creación de la reseña y detalles de la reseña creada.

#### Actualización de Reseña
- **Método**: PUT
- **Ruta**: `/reviews/{reviewId}`
- **Descripción**: Permite a un usuario actualizar una reseña existente.
- **Request Body**: Datos actualizados de la reseña, incluyendo `rating`, `comment`.
- **Response**: Confirmación de la actualización de la reseña y detalles de la reseña actualizada.

#### Eliminación de Reseña
- **Método**: DELETE
- **Ruta**: `/reviews/{reviewId}`
- **Descripción**: Permite a un usuario eliminar una reseña existente.
- **Response**: Confirmación de la eliminación de la reseña.

#### Consulta de Reseñas por Producto
- **Método**: GET
- **Ruta**: `/products/{productId}/reviews`
- **Descripción**: Recupera todas las reseñas asociadas a un producto específico.
- **Response**: Lista de reseñas para el producto, incluyendo calificaciones y comentarios.

#### Consulta de Reseñas por Usuario
- **Método**: GET
- **Ruta**: `/users/{userId}/reviews`
- **Descripción**: Recupera todas las reseñas escritas por un usuario específico.
- **Response**: Lista de reseñas escritas por el usuario, incluyendo productos revisados y calificaciones.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Las reseñas pueden variar en formato y pueden incluir texto libre, lo que se adapta bien a la flexibilidad de las bases de datos NoSQL.

### Integraciones
- **Microservicio de Productos**: Para recuperar información sobre los productos al mostrar reseñas.
- **Microservicio de Usuarios**: Para asociar reseñas con los usuarios que las escribieron.

### Consideraciones Adicionales
- **Moderación**: Implementar mecanismos para moderar y revisar reseñas antes de su publicación para evitar contenido inapropiado.
- **Escalabilidad**: Considerar la carga de trabajo y la frecuencia de las actualizaciones y consultas para asegurar la escalabilidad del servicio.
- **Seguridad**: Asegurar que solo los usuarios autorizados puedan actualizar o eliminar sus propias reseñas.

