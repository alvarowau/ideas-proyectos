# Microservicio de Gestión de Pedidos

## Descripción
El microservicio de Gestión de Pedidos se encarga de la administración de los pedidos realizados por los usuarios. Esto incluye la creación, actualización, eliminación y consulta de pedidos. Además, gestiona la información relacionada con los artículos del pedido, los detalles de envío, y el estado del pedido.

### Clases `enum`
- **OrderStatus**: Enum para representar el estado del pedido. Ejemplo:
  - **PENDING**: Pendiente.
  - **SHIPPED**: Enviado.
  - **DELIVERED**: Entregado.
  - **CANCELLED**: Cancelado.

### Persistencia en la Base de Datos
- **Pedidos**: Información sobre los pedidos realizados.
  - `orderId`: Identificador único del pedido.
  - `buyerId`: Referencia al identificador del usuario que realizó el pedido (relacionado con la clase `User`).
  - `totalAmount`: Monto total del pedido.
  - `orderDate`: Fecha en la que se realizó el pedido.
  - `status`: Estado del pedido (almacenado como referencia al `enum OrderStatus`).
  - `shippingId`: Referencia a los detalles de envío (relacionado con la clase `ShippingDetails`).
  - `paymentId`: Referencia a los detalles de pago (relacionado con la clase `PaymentDetails`).

- **OrderItem**: Información sobre los artículos incluidos en el pedido.
  - `orderItemId`: Identificador único del artículo del pedido.
  - `productId`: Referencia al identificador del producto (relacionado con la clase `Product`).
  - `quantity`: Cantidad del producto en el pedido.
  - `price`: Precio del producto en el momento del pedido.

### Clases Relacionadas
- **User**: Clase que representa al usuario que realiza el pedido.
- **ShippingDetails**: Clase que contiene información sobre el envío del pedido. Contiene:
  - `shippingId`: Identificador único de los detalles de envío.
  - `address`: Dirección de envío.
  - `carrier`: Nombre del transportista.
  - `shippingCost`: Costo del envío.
  - `trackingNumber`: Número de seguimiento del envío.
  - `estimatedDelivery`: Fecha estimada de entrega.

- **PaymentDetails**: Clase que contiene información sobre el pago del pedido. Contiene:
  - `paymentId`: Identificador único de los detalles de pago.
  - `paymentMethod`: Método de pago utilizado.
  - `transactionId`: ID de la transacción.
  - `amountPaid`: Monto pagado.
  - `paymentDate`: Fecha del pago.

### Endpoints

#### Creación de Pedido
- **Método**: POST
- **Ruta**: `/orders`
- **Descripción**: Crea un nuevo pedido en el sistema.
- **Request Body**: Datos del pedido, incluyendo artículos, detalles de envío y pago.
- **Response**: Detalles del pedido creado.

#### Actualización de Pedido
- **Método**: PUT
- **Ruta**: `/orders/{orderId}`
- **Descripción**: Actualiza la información de un pedido existente.
- **Request Body**: Datos actualizados del pedido.
- **Response**: Detalles del pedido actualizado.

#### Eliminación de Pedido
- **Método**: DELETE
- **Ruta**: `/orders/{orderId}`
- **Descripción**: Elimina un pedido del sistema.
- **Response**: Confirmación de eliminación.

#### Consulta de Pedido
- **Método**: GET
- **Ruta**: `/orders/{orderId}`
- **Descripción**: Recupera la información de un pedido específico.
- **Response**: Detalles del pedido solicitado.

#### Listado de Pedidos
- **Método**: GET
- **Ruta**: `/orders`
- **Descripción**: Recupera una lista de todos los pedidos.
- **Response**: Lista de pedidos.

### Base de Datos
- **Elección**: SQL
- **Motivo**: La información de pedidos requiere manejo de transacciones y consistencia entre entidades relacionadas (usuarios, artículos, detalles de envío y pago).

### Integraciones
- **Microservicio de Productos**: Para consultar la disponibilidad de productos en relación con los pedidos y actualizar stock.
- **Microservicio de Usuarios**: Para obtener información sobre el usuario que realiza el pedido.
- **Microservicio de Envíos**: Para obtener y actualizar detalles de envío relacionados con los pedidos.
- **Microservicio de Pagos**: Para gestionar y verificar detalles de pago de los pedidos.

### Consideraciones Adicionales
- **Transacciones**: Asegurar que la creación y actualización de pedidos maneje transacciones de manera robusta para mantener la integridad de los datos.
- **Validación**: Verificar que todos los datos necesarios (productos, detalles de envío, pago) sean correctos antes de confirmar un pedido.
- **Estado del Pedido**: Implementar lógica para actualizar el estado del pedido y notificar a los usuarios sobre cambios en el estado.

