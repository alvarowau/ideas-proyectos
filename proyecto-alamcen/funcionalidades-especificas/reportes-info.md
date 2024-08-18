# Microservicio de Reportes

## Descripción
El microservicio de Reportes se encarga de generar, almacenar y gestionar diversos tipos de informes relacionados con las operaciones del sistema. Los reportes pueden incluir análisis de ventas, comportamiento del usuario, inventario, entre otros, y son utilizados para la toma de decisiones estratégicas y operativas.

### Clases `enum`
- **ReportType**: Enum para representar los diferentes tipos de reportes que se pueden generar.
  - **SALES_REPORT**: Reporte de ventas.
  - **USER_ACTIVITY_REPORT**: Reporte de actividad del usuario.
  - **INVENTORY_REPORT**: Reporte de inventario.
  - **FINANCIAL_REPORT**: Reporte financiero.
  - **PERFORMANCE_REPORT**: Reporte de rendimiento.

### Persistencia en la Base de Datos
- **Report**: Clase que representa un reporte generado por el sistema.
  - `reportId`: Identificador único del reporte.
  - `title`: Título del reporte.
  - `description`: Descripción del reporte.
  - `creationDate`: Fecha de creación del reporte.
  - `reportType`: Tipo de reporte (`SALES_REPORT`, `USER_ACTIVITY_REPORT`, etc.).
  - `content`: Contenido del reporte, que puede ser en diferentes formatos como texto, JSON, etc.
  - `generatedBy`: Identificador del usuario o sistema que generó el reporte (opcional).

### Clases Relacionadas
- **User**: Clase que representa a un usuario del sistema. Contiene:
  - `userId`: Identificador único del usuario.

### Endpoints

#### Generación de Reporte
- **Método**: POST
- **Ruta**: `/reports/generate`
- **Descripción**: Genera un nuevo reporte basado en los parámetros proporcionados.
- **Request Body**: Datos requeridos para la generación del reporte, incluyendo `reportType`, `title`, `description`, y cualquier filtro o criterio necesario.
- **Response**: Detalles del reporte generado, incluyendo `reportId` y `creationDate`.

#### Consulta de Reportes
- **Método**: GET
- **Ruta**: `/reports`
- **Descripción**: Recupera una lista de reportes generados en el sistema.
- **Query Parameters**: 
  - `reportType` (opcional): Filtrar por el tipo de reporte.
  - `dateFrom` (opcional): Filtrar por fecha desde.
  - `dateTo` (opcional): Filtrar por fecha hasta.
  - `generatedBy` (opcional): Filtrar por el usuario que generó el reporte.
- **Response**: Lista de reportes que coinciden con los filtros aplicados.

#### Consulta de Reporte Específico
- **Método**: GET
- **Ruta**: `/reports/{reportId}`
- **Descripción**: Recupera los detalles de un reporte específico, incluyendo su contenido.
- **Response**: Detalles completos del reporte.

#### Eliminación de Reporte
- **Método**: DELETE
- **Ruta**: `/reports/{reportId}`
- **Descripción**: Elimina un reporte específico del sistema.
- **Response**: Confirmación de la eliminación del reporte.

### Base de Datos
- **Elección**: NoSQL
- **Motivo**: Los reportes pueden tener estructuras de datos variadas y contener grandes volúmenes de información. NoSQL ofrece la flexibilidad y escalabilidad necesarias para manejar estos requisitos de manera eficiente.

### Integraciones
- **Microservicio de Gestión de Pedidos**: Para generar reportes relacionados con ventas y órdenes.
- **Microservicio de Gestión de Inventario**: Para reportes sobre niveles de stock y rotación de productos.
- **Microservicio de Usuarios**: Para reportes sobre actividad de usuarios y análisis de comportamiento.

### Consideraciones Adicionales
- **Programación de Reportes**: Implementar la capacidad de programar la generación automática de reportes en intervalos regulares.
- **Seguridad**: Asegurar que solo usuarios autorizados puedan acceder y generar reportes confidenciales.
- **Exportación de Reportes**: Proveer funcionalidades para exportar los reportes en diferentes formatos (e.g., PDF, CSV, Excel).
- **Almacenamiento a Largo Plazo**: Definir políticas de retención y archivado de reportes, considerando el espacio de almacenamiento y las necesidades legales.

