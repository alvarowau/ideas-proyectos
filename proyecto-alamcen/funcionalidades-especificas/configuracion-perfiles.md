## Configuración de Perfiles en Spring

### 1. Crear Archivos de Configuración para Perfiles

Se han creado archivos de configuración específicos para cada entorno:

- **application-dev.properties**: Configuración para el entorno de desarrollo.
- **application-prod.properties**: Configuración para el entorno de producción.

#### Ejemplo de Configuración:

- **application-dev.properties**:
    ```properties
    spring.datasource.url=jdbc:h2:mem:devdb
    spring.datasource.driverClassName=org.h2.Driver
    spring.datasource.username=sa
    spring.datasource.password=password
    spring.jpa.hibernate.ddl-auto=create-drop
    spring.h2.console.enabled=true
    ```

- **application-prod.properties**:
    ```properties
    spring.datasource.url=jdbc:mysql://localhost:3306/proddb
    spring.datasource.driverClassName=com.mysql.cj.jdbc.Driver
    spring.datasource.username=produser
    spring.datasource.password=prodpassword
    spring.jpa.hibernate.ddl-auto=update
    spring.h2.console.enabled=false
    ```

### 2. Configuración del Perfil Activo

- **En el archivo `application.properties` principal**:
    ```properties
    spring.profiles.active=dev
    ```

- **En la Línea de Comandos**:
    ```shell
    java -jar storelinkplatform.jar --spring.profiles.active=prod
    ```

### 3. Gestión de Perfiles

La gestión de perfiles permite cambiar entre diferentes configuraciones de entorno fácilmente, asegurando que la aplicación se ejecute correctamente en desarrollo, pruebas, y producción.
