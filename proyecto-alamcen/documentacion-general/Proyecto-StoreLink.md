# Proyecto StoreLink

StoreLink es un sistema de gestión de almacenes y ventas en línea diseñado para facilitar la administración de inventarios, pedidos, usuarios y más. El sistema está estructurado en microservicios para una gestión eficiente y escalable.

## Microservicio de Gestión de Usuarios

**Responsabilidades:**
- Gestión de perfiles de usuario.
- Roles y permisos.
- Autenticación y autorización.

**Componentes:**
- **Modelo**:
  - `User`
  - `Address` (para direcciones de usuario)
- **Repositorio**:
  - `UserRepository`
- **Servicio**:
  - `UserService`
- **Controlador**:
  - `UserController`
- **Pruebas Unitarias**:
  - Pruebas para `UserService`, `UserController`, etc.
- **Base de Datos:** SQL (para integridad y seguridad en la gestión de usuarios)

## Microservicio de Gestión de Productos

**Responsabilidades:**
- Gestión de productos.
- Manejo de categorías y proveedores.
- Gestión de imágenes de productos.

**Componentes:**
- **Modelo**:
  - `Product`
  - `Category`
  - `Supplier`
  - `Image`
- **Repositorio**:
  - `ProductRepository`
  - `CategoryRepository`
  - `SupplierRepository`
- **Servicio**:
  - `ProductService`
  - `CategoryService`
  - `SupplierService`
- **Controlador**:
  - `ProductController`
  - `CategoryController`
  - `SupplierController`
- **Pruebas Unitarias**:
  - Pruebas para `ProductService`, `ProductController`, etc.
- **Base de Datos:** SQL para datos estructurados y relaciones complejas; NoSQL para imágenes de productos

## Microservicio de Gestión de Pedidos

**Responsabilidades:**
- Gestión de pedidos y artículos de pedidos.
- Procesamiento de pagos y envíos.
- Manejo de devoluciones y seguimiento.

**Componentes:**
- **Modelo**:
  - `Order`
  - `OrderItem`
  - `ShippingDetails`
  - `PaymentDetails`
  - `Return`
  - `Tracking`
  - `Invoice`
- **Repositorio**:
  - `OrderRepository`
  - `ReturnRepository`
  - `TrackingRepository`
  - `InvoiceRepository`
- **Servicio**:
  - `OrderService`
  - `ReturnService`
  - `TrackingService`
  - `InvoiceService`
- **Controlador**:
  - `OrderController`
  - `ReturnController`
  - `TrackingController`
  - `InvoiceController`
- **Pruebas Unitarias**:
  - Pruebas para `OrderService`, `OrderController`, etc.
- **Base de Datos:** SQL para la gestión de pedidos y transacciones financieras; NoSQL para el seguimiento de paquetes y devoluciones

## Microservicio de Gestión de Inventario

**Responsabilidades:**
- Control del stock de productos.
- Gestión de ubicaciones en el almacén.

**Componentes:**
- **Modelo**:
  - `Product` (puede ser una referencia o parte del microservicio de productos)
  - `Location`
- **Repositorio**:
  - `InventoryRepository`
  - `LocationRepository`
- **Servicio**:
  - `InventoryService`
- **Controlador**:
  - `InventoryController`
- **Pruebas Unitarias**:
  - Pruebas para `InventoryService`, `InventoryController`, etc.
- **Base de Datos:** SQL para el control de inventario y ubicaciones

## Microservicio de Carrito de Compras

**Responsabilidades:**
- Gestión del carrito de compras de los usuarios.

**Componentes:**
- **Modelo**:
  - `Cart`
  - `CartItem`
- **Repositorio**:
  - `CartRepository`
- **Servicio**:
  - `CartService`
- **Controlador**:
  - `CartController`
- **Pruebas Unitarias**:
  - Pruebas para `CartService`, `CartController`, etc.
- **Base de Datos:** NoSQL para flexibilidad en el manejo del carrito de compras

## Microservicio de Reseñas y Valoraciones

**Responsabilidades:**
- Gestión de reseñas y valoraciones de productos.

**Componentes:**
- **Modelo**:
  - `Review`
- **Repositorio**:
  - `ReviewRepository`
- **Servicio**:
  - `ReviewService`
- **Controlador**:
  - `ReviewController`
- **Pruebas Unitarias**:
  - Pruebas para `ReviewService`, `ReviewController`, etc.
- **Base de Datos:** NoSQL para flexibilidad en el manejo de datos no estructurados

## Microservicio de Promociones y Descuentos

**Responsabilidades:**
- Gestión de códigos de descuento y promociones aplicables a productos.

**Componentes:**
- **Modelo**:
  - `Discount`
- **Repositorio**:
  - `DiscountRepository`
- **Servicio**:
  - `DiscountService`
- **Controlador**:
  - `DiscountController`
- **Pruebas Unitarias**:
  - Pruebas para `DiscountService`, `DiscountController`, etc.
- **Base de Datos:** NoSQL para flexibilidad en la gestión de promociones y descuentos

## Microservicio de Notificaciones

**Responsabilidades:**
- Envío y gestión de notificaciones a los usuarios.

**Componentes:**
- **Modelo**:
  - `Notification`
- **Repositorio**:
  - `NotificationRepository`
- **Servicio**:
  - `NotificationService`
- **Controlador**:
  - `NotificationController`
- **Pruebas Unitarias**:
  - Pruebas para `NotificationService`, `NotificationController`, etc.
- **Base de Datos:** NoSQL para manejar altos volúmenes de notificaciones

## Microservicio de Auditoría

**Responsabilidades:**
- Registro de acciones importantes en el sistema para auditoría.

**Componentes:**
- **Modelo**:
  - `AuditLog`
- **Repositorio**:
  - `AuditLogRepository`
- **Servicio**:
  - `AuditLogService`
- **Controlador**:
  - `AuditLogController`
- **Pruebas Unitarias**:
  - Pruebas para `AuditLogService`, `AuditLogController`, etc.
- **Base de Datos:** NoSQL para manejar grandes volúmenes de registros de auditoría

## Microservicio de Reportes

**Responsabilidades:**
- Generación y gestión de informes.

**Componentes:**
- **Modelo**:
  - `Report`
- **Repositorio**:
  - `ReportRepository`
- **Servicio**:
  - `ReportService`
- **Controlador**:
  - `ReportController`
- **Pruebas Unitarias**:
  - Pruebas para `ReportService`, `ReportController`, etc.
- **Base de Datos:** NoSQL para manejar datos de reportes con formatos variados

## Posibles Ajustes o Adiciones

- **Microservicio de Configuración**: Para manejar configuraciones globales del sistema, como parámetros de la tienda, integraciones de terceros, etc.
- **Microservicio de Seguridad**: Para manejar aspectos específicos de seguridad, como autenticación y autorización, que pueden ser reutilizables en diferentes microservicios.

Este enfoque modular permite que cada microservicio sea independiente, escalable y fácil de mantener. Puedes adaptar y ajustar estos servicios según las necesidades específicas de tu proyecto.
