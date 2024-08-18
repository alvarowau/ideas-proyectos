## Microservicio de Configuración

### Descripción
El Microservicio de Configuración se encarga de manejar configuraciones globales del sistema, tales como parámetros de la tienda, configuraciones de integraciones de terceros, y otras preferencias del sistema que deben ser centralizadas y gestionadas de forma coherente.

### Clases `enum`
- **ConfigurationType**: Enum para representar los diferentes tipos de configuraciones que se pueden manejar.
  - **STORE_SETTINGS**: Configuraciones generales de la tienda (e.g., nombre de la tienda, dirección, horario de atención).
  - **THIRD_PARTY_INTEGRATIONS**: Configuraciones para integraciones con sistemas de terceros (e.g., pasarelas de pago, servicios de envío).
  - **SECURITY_SETTINGS**: Configuraciones relacionadas con la seguridad (e.g., políticas de contraseña, autenticación de dos factores).
  - **UI_SETTINGS**: Configuraciones de la interfaz de usuario (e.g., temas, idiomas).

### Persistencia en la Base de Datos
- **Configuration**: Clase que representa una configuración del sistema.
  - `configId`: Identificador único de la configuración.
  - `name`: Nombre de la configuración.
  - `value`: Valor de la configuración.
  - `type`: Tipo de configuración (`STORE_SETTINGS`, `THIRD_PARTY_INTEGRATIONS`, etc.).
  - `lastUpdated`: Fecha de la última actualización de la configuración.

### Endpoints

#### Consultar Configuraciones
- **Método**: GET
- **Ruta**: `/configurations`
- **Descripción**: Recupera una lista de configuraciones globales del sistema.
- **Query Parameters**:
  - `type` (opcional): Filtrar por tipo de configuración.
- **Response**: Lista de configuraciones que coinciden con los filtros aplicados.

#### Consultar Configuración Específica
- **Método**: GET
- **Ruta**: `/configurations/{configId}`
- **Descripción**: Recupera los detalles de una configuración específica.
- **Response**: Detalles de la configuración solicitada.

#### Actualizar Configuración
- **Método**: PUT
- **Ruta**: `/configurations/{configId}`
- **Descripción**: Actualiza el valor de una configuración existente.
- **Request Body**: 
  - `name`: Nombre de la configuración.
  - `value`: Valor actualizado de la configuración.
- **Response**: Confirmación de la actualización de la configuración.

#### Crear Nueva Configuración
- **Método**: POST
- **Ruta**: `/configurations`
- **Descripción**: Crea una nueva configuración en el sistema.
- **Request Body**:
  - `name`: Nombre de la configuración.
  - `value`: Valor de la configuración.
  - `type`: Tipo de configuración.
- **Response**: Detalles de la nueva configuración creada.

#### Eliminar Configuración
- **Método**: DELETE
- **Ruta**: `/configurations/{configId}`
- **Descripción**: Elimina una configuración específica del sistema.
- **Response**: Confirmación de la eliminación de la configuración.

