# Microservicio de Gestión de Promociones

## Descripción
El microservicio de Gestión de Promociones se encarga de manejar las promociones y descuentos aplicables a productos y pedidos. Este servicio permite crear, actualizar, eliminar y consultar promociones activas y sus detalles.

### Clases `enum`
- **DiscountType**: Enum para representar el tipo de descuento.
  - **PERCENTAGE**: Descuento en porcentaje.
  - **FIXED_AMOUNT**: Descuento en cantidad fija.

### Persistencia en la Base de Datos
- **Discount**: Información sobre una promoción o descuento.
  - `discountId`: Identificador único del descuento.
  - `code`: Código de descuento que los usuarios pueden ingresar.
  - `discountValue`: Valor del descuento, representado en porcentaje o cantidad fija (dependiendo del `discountType`).
  - `discountType`: Tipo de descuento (`PERCENTAGE` o `FIXED_AMOUNT`).
  - `startDate`: Fecha de inicio de la promoción.
  - `endDate`: Fecha de finalización de la promoción.
  - `description`: Descripción opcional de la promoción.
  - `applicableProducts`: Lista de identificadores de productos a los que se aplica el descuento.

### Clases Relacionadas
- **Product**: Clase que representa un producto. Contiene:
  - `productId`: Identificador único del producto.

### Endpoints

#### Creación de Promoción
- **Método**: POST
- **Ruta**: `/discounts`
- **Descripción**: Permite crear una nueva promoción o descuento.
- **Request Body**: Datos de la promoción, incluyendo `code`, `discountValue`, `discountType`, `startDate`, `endDate`, `description`, y `applicableProducts`.
- **Response**: Confirmación de la creación de la promoción y detalles de la promoción creada.

#### Actualización de Promoción
- **Método**: PUT
- **Ruta**: `/discounts/{discountId}`
- **Descripción**: Permite actualizar una promoción existente.
- **Request Body**: Datos actualizados de la promoción, incluyendo `code`, `discountValue`, `discountType`, `startDate`, `endDate`, `description`, y `applicableProducts`.
- **Response**: Confirmación de la actualización de la promoción y detalles de la promoción actualizada.

#### Eliminación de Promoción
- **Método**: DELETE
- **Ruta**: `/discounts/{discountId}`
- **Descripción**: Permite eliminar una promoción existente.
- **Response**: Confirmación de la eliminación de la promoción.

#### Consulta de Promociones Activas
- **Método**: GET
- **Ruta**: `/discounts`
- **Descripción**: Recupera todas las promociones activas.
- **Response**: Lista de promociones activas, incluyendo detalles como `code`, `discountValue`, `discountType`, `startDate`, `endDate`, y `description`.

#### Consulta de Promociones por Producto
- **Método**: GET
- **Ruta**: `/products/{productId}/discounts`
- **Descripción**: Recupera todas las promociones aplicables a un producto específico.
- **Response**: Lista de promociones aplicables al producto, incluyendo `code`, `discountValue`, `discountType`, y `description`.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Las promociones pueden variar en formato y frecuencia, y NoSQL ofrece flexibilidad para gestionar datos diversos y escalabilidad para operaciones de alta carga.

### Integraciones
- **Microservicio de Productos**: Para aplicar descuentos a productos y consultar promociones activas.
- **Microservicio de Pedidos**: Para aplicar descuentos durante el proceso de compra y facturación.

### Consideraciones Adicionales
- **Validación de Fechas**: Asegurar que las promociones sean válidas solo dentro del rango de fechas especificado.
- **Aplicabilidad de Descuentos**: Implementar lógica para verificar si un descuento es aplicable a un producto o pedido específico.
- **Escalabilidad**: Considerar la carga de trabajo y la frecuencia de actualizaciones y consultas para asegurar la escalabilidad del servicio.
- **Seguridad**: Asegurar que los datos de las promociones no se vean comprometidos y que solo usuarios autorizados puedan modificar o eliminar promociones.

