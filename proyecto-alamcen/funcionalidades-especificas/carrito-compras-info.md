# Microservicio de Gestión de Carritos

## Descripción
El microservicio de Gestión de Carritos se encarga de la administración de los carritos de compras de los usuarios. Esto incluye la adición y eliminación de productos en el carrito, así como la actualización de la cantidad de cada producto y el cálculo del monto total.

### Clases `enum`
- **CartStatus**: Enum para representar el estado del carrito. Ejemplo:
  - **ACTIVE**: Carrito activo, en proceso de compra.
  - **ABANDONED**: Carrito que no ha sido completado ni revisado en un tiempo.
  - **COMPLETED**: Carrito convertido en un pedido.

### Persistencia en la Base de Datos
- **Cart**: Información sobre el carrito de compras.
  - `cartId`: Identificador único del carrito.
  - `userId`: Identificador del usuario asociado con el carrito (relacionado con la clase `User`).
  - `status`: Estado del carrito (almacenado como referencia al `enum CartStatus`).
  - `totalAmount`: Monto total de los artículos en el carrito.

- **CartItem**: Información sobre los artículos dentro del carrito.
  - `cartItemId`: Identificador único del artículo en el carrito.
  - `cartId`: Identificador del carrito al que pertenece el artículo (relacionado con la clase `Cart`).
  - `productId`: Identificador del producto (relacionado con la clase `Product`).
  - `quantity`: Cantidad del producto en el carrito.
  - `price`: Precio del producto al momento de ser añadido al carrito.

### Clases Relacionadas
- **User**: Clase que representa al usuario. Contiene:
  - `userId`: Identificador único del usuario.
  - `username`: Nombre de usuario.
  - `role`: Rol del usuario.

- **Product**: Clase que representa un producto. Contiene:
  - `productId`: Identificador único del producto.
  - `name`: Nombre del producto.
  - `price`: Precio del producto.

### Endpoints

#### Adición de Producto al Carrito
- **Método**: POST
- **Ruta**: `/cart/{cartId}/items`
- **Descripción**: Añade un producto al carrito con una cantidad específica.
- **Request Body**: Datos del producto (productId) y la cantidad.
- **Response**: Confirmación de la adición y detalles del carrito actualizado.

#### Eliminación de Producto del Carrito
- **Método**: DELETE
- **Ruta**: `/cart/{cartId}/items/{cartItemId}`
- **Descripción**: Elimina un artículo específico del carrito.
- **Response**: Confirmación de la eliminación y detalles del carrito actualizado.

#### Actualización de Cantidad de Producto
- **Método**: PUT
- **Ruta**: `/cart/{cartId}/items/{cartItemId}`
- **Descripción**: Actualiza la cantidad de un producto específico en el carrito.
- **Request Body**: Nueva cantidad del producto.
- **Response**: Confirmación de la actualización y detalles del carrito actualizado.

#### Consulta del Carrito
- **Método**: GET
- **Ruta**: `/cart/{cartId}`
- **Descripción**: Recupera los detalles del carrito, incluyendo los artículos y el monto total.
- **Response**: Información del carrito, incluyendo los artículos y el total.

#### Conversión de Carrito a Pedido
- **Método**: POST
- **Ruta**: `/cart/{cartId}/checkout`
- **Descripción**: Convierte un carrito en un pedido, procesando la compra.
- **Request Body**: Información adicional necesaria para completar la compra (por ejemplo, dirección de envío).
- **Response**: Confirmación del pedido creado y detalles del pedido.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Los carritos son entidades dinámicas y pueden tener estructuras de datos variables, lo que se adapta bien a las bases de datos NoSQL.

### Integraciones
- **Microservicio de Productos**: Para obtener detalles del producto y verificar la disponibilidad al añadir artículos al carrito.
- **Microservicio de Pedidos**: Para convertir carritos en pedidos y sincronizar la información del carrito con el sistema de pedidos.
- **Microservicio de Usuarios**: Para asociar carritos con usuarios y verificar el estado de los carritos de los usuarios.

### Consideraciones Adicionales
- **Persistencia Temporal**: Los carritos pueden ser temporales y pueden necesitar persistencia entre sesiones, especialmente si los usuarios están registrados.
- **Sincronización**: Asegurar la sincronización de carritos entre dispositivos del mismo usuario, si es necesario.
- **Validación de Productos**: Verificar la disponibilidad de los productos y la validez de los precios antes de completar el carrito.

