# Microservicio de Gestión de Productos

## Descripción
El microservicio de Gestión de Productos se encarga de la administración de los productos en el sistema. Esto incluye la adición, actualización, eliminación, y consulta de productos. Este servicio también maneja la relación entre productos, categorías, y proveedores.

### Clases `enum`
- **Category**: Enum para representar las categorías de productos. Ejemplo:
  - **ELECTRONICS**: Electrónicos.
  - **FASHION**: Moda.
  - **HOME**: Hogar.
  - **BOOKS**: Libros.

### Persistencia en la Base de Datos
- **Productos**: Información detallada sobre los productos.
  - `productId`: Identificador único para el producto.
  - `name`: Nombre del producto.
  - `description`: Descripción del producto.
  - `sku`: Código SKU, un código único para el seguimiento.
  - `price`: Precio del producto.
  - `quantity`: Cantidad disponible en stock.
  - `category`: Categoría a la que pertenece el producto (almacenada como referencia al `enum Category`).
  - `locationId`: Referencia al identificador de la ubicación del producto en el almacén (relacionado con la clase `Location`).
  - `supplierId`: Referencia al identificador del proveedor (relacionado con la clase `Supplier`).

### Clases Relacionadas
- **Location**: Clase que maneja la ubicación física del producto en el almacén. Contiene:
  - `locationId`: Identificador único para la ubicación.
  - `section`: Sección del almacén.
  - `aisle`: Número de pasillo.
  - `shelf`: Número de estante.
  - `bin`: Número de contenedor.

- **Supplier**: Clase que representa al proveedor del producto. Contiene:
  - `supplierId`: Identificador único del proveedor.
  - `name`: Nombre del proveedor.
  - `contactInfo`: Información de contacto del proveedor.

### Endpoints

#### Adición de Producto
- **Método**: POST
- **Ruta**: `/products`
- **Descripción**: Agrega un nuevo producto al sistema.
- **Request Body**: Datos del producto a agregar.
- **Response**: Detalles del producto creado.

#### Actualización de Producto
- **Método**: PUT
- **Ruta**: `/products/{productId}`
- **Descripción**: Actualiza la información de un producto existente.
- **Request Body**: Datos actualizados del producto.
- **Response**: Detalles del producto actualizado.

#### Eliminación de Producto
- **Método**: DELETE
- **Ruta**: `/products/{productId}`
- **Descripción**: Elimina un producto del sistema.
- **Response**: Confirmación de eliminación.

#### Consulta de Productos
- **Método**: GET
- **Ruta**: `/products/{productId}`
- **Descripción**: Recupera la información de un producto específico.
- **Response**: Detalles del producto solicitado.

#### Listado de Productos
- **Método**: GET
- **Ruta**: `/products`
- **Descripción**: Recupera una lista de todos los productos.
- **Response**: Lista de productos.

### Base de Datos
- **Elección**: SQL
- **Motivo**: La información de productos es estructurada y se requiere integridad relacional para mantener relaciones consistentes con categorías, proveedores y ubicaciones.

### Integraciones
- **Microservicio de Pedidos**: Para consultar la disponibilidad de productos en relación con los pedidos.
- **Microservicio de Usuarios**: Para gestionar los productos que los usuarios pueden administrar o comprar.
- **Microservicio de Ubicación**: Para obtener y actualizar la ubicación de los productos en el almacén.
- **Microservicio de Proveedores**: Para obtener información sobre los proveedores asociados con los productos.

### Consideraciones Adicionales
- **Validación de Datos**: Asegurar que los datos del producto sean válidos y completos antes de la adición o actualización.
- **Imágenes de Productos**: Aunque las imágenes no se gestionan directamente en este microservicio, se relacionan con productos a través del microservicio de Imágenes.
- **Categorías y Proveedores**: La relación con categorías y proveedores debe ser gestionada cuidadosamente para asegurar la integridad referencial.

