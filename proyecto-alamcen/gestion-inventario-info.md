# Microservicio de Gestión de Inventario

## Descripción
El microservicio de Gestión de Inventario se encarga de la administración y control del inventario en el almacén. Esto incluye la gestión de la ubicación de los productos, la cantidad disponible, y la actualización de la información del inventario en función de las operaciones de entrada y salida de productos.

### Clases `enum`
- **InventoryAction**: Enum para representar las acciones realizadas en el inventario. Ejemplo:
  - **ADDITION**: Adición de productos al inventario.
  - **REMOVAL**: Eliminación de productos del inventario.
  - **TRANSFER**: Transferencia de productos entre ubicaciones.

### Persistencia en la Base de Datos
- **Products**: Información sobre los productos en el inventario.
  - `productId`: Identificador único del producto.
  - `name`: Nombre del producto.
  - `description`: Descripción del producto.
  - `sku`: Código SKU del producto.
  - `price`: Precio del producto.
  - `quantity`: Cantidad disponible en stock.
  - `categoryId`: Identificador de la categoría a la que pertenece el producto (relacionado con la clase `Category`).

- **Location**: Información sobre las ubicaciones en el almacén.
  - `locationId`: Identificador único de la ubicación.
  - `section`: Sección del almacén.
  - `aisle`: Número del pasillo.
  - `shelf`: Número del estante.
  - `bin`: Número del contenedor.

- **InventoryLog**: Información sobre las operaciones realizadas en el inventario.
  - `logId`: Identificador único del registro de inventario.
  - `productId`: Identificador del producto.
  - `locationId`: Identificador de la ubicación.
  - `action`: Acción realizada (almacenado como referencia al `enum InventoryAction`).
  - `quantity`: Cantidad afectada por la acción.
  - `timestamp`: Fecha y hora de la acción.
  - `userId`: Identificador del usuario que realizó la acción (relacionado con la clase `User`).

### Clases Relacionadas
- **Product**: Clase que representa un producto. Contiene:
  - `productId`: Identificador único del producto.
  - `name`: Nombre del producto.
  - `description`: Descripción del producto.
  - `sku`: Código SKU.
  - `price`: Precio.
  - `quantity`: Cantidad disponible.
  - `categoryId`: Identificador de la categoría.
  - `supplierId`: Identificador del proveedor.

- **Location**: Clase que representa una ubicación en el almacén. Contiene:
  - `locationId`: Identificador único.
  - `section`: Sección.
  - `aisle`: Pasillo.
  - `shelf`: Estante.
  - `bin`: Contenedor.

- **User**: Clase que representa a un usuario que realiza operaciones de inventario. Contiene:
  - `userId`: Identificador único del usuario.
  - `username`: Nombre de usuario.
  - `role`: Rol del usuario (por ejemplo, Administrador, Almacén).

### Endpoints

#### Adición de Producto al Inventario
- **Método**: POST
- **Ruta**: `/inventory/add`
- **Descripción**: Añade productos al inventario en una ubicación específica.
- **Request Body**: Datos del producto y la ubicación, incluyendo la cantidad a añadir.
- **Response**: Confirmación de la adición y detalles del registro de inventario.

#### Eliminación de Producto del Inventario
- **Método**: POST
- **Ruta**: `/inventory/remove`
- **Descripción**: Elimina productos del inventario desde una ubicación específica.
- **Request Body**: Datos del producto y la ubicación, incluyendo la cantidad a eliminar.
- **Response**: Confirmación de la eliminación y detalles del registro de inventario.

#### Transferencia de Producto
- **Método**: POST
- **Ruta**: `/inventory/transfer`
- **Descripción**: Transfiere productos entre ubicaciones del almacén.
- **Request Body**: Datos del producto, ubicación de origen, ubicación de destino, y cantidad a transferir.
- **Response**: Confirmación de la transferencia y detalles del registro de inventario.

#### Consulta de Inventario
- **Método**: GET
- **Ruta**: `/inventory`
- **Descripción**: Recupera la información del inventario, incluyendo la cantidad disponible en cada ubicación.
- **Response**: Lista de productos con su cantidad en stock y ubicación.

### Base de Datos
- **Elección**: SQL
- **Motivo**: La gestión de inventario requiere consistencia y relaciones complejas entre productos, ubicaciones y operaciones, lo cual es bien soportado por bases de datos SQL.

### Integraciones
- **Microservicio de Productos**: Para obtener detalles de productos y actualizar la cantidad disponible en el inventario.
- **Microservicio de Pedidos**: Para actualizar el inventario basado en las órdenes realizadas (entrada y salida de productos).
- **Microservicio de Ubicaciones**: Para gestionar y consultar ubicaciones en el almacén.

### Consideraciones Adicionales
- **Transacciones**: Asegurar que todas las operaciones (adición, eliminación, transferencia) sean transaccionadas para mantener la integridad del inventario.
- **Historial**: Mantener un registro detallado de todas las operaciones de inventario para auditoría y trazabilidad.
- **Validación**: Verificar la disponibilidad del producto antes de permitir operaciones de eliminación o transferencia.

