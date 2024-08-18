## Configuración Inicial del Proyecto

### Proyecto Padre

1. **Creación del Proyecto Padre**:
   - Se utilizó [Spring Initializr](https://start.spring.io/) para generar el proyecto padre.
   - Configuraciones:
     - **Group**: `com.alvarowau`
     - **Artifact**: `storelinkplatform`
     - **Name**: `StoreLinkPlatform`
     - **Packaging**: `pom` (Definido como proyecto padre)
     - **Java Version**: 21

2. **Dependencias Comunes**:
   - Se añadieron las siguientes dependencias comunes en el archivo `pom.xml` del proyecto padre:
     - **`spring-boot-starter-web`**: Para crear servicios RESTful.
     - **`spring-boot-starter-data-jpa`**: Para la persistencia de datos con JPA.
     - **`h2`**: Base de datos en memoria para pruebas.
     - **`spring-boot-devtools`**: Herramientas para facilitar el desarrollo.

3. **Estructura de Módulos**:
   - El proyecto está configurado para incluir módulos adicionales. Estos se agregarán en la sección `<modules>` del `pom.xml` del proyecto padre. Cada módulo representará una parte específica de la aplicación (como productos, usuarios, pedidos, etc.).

4. **Repositorio Git**:
   - El proyecto padre fue subido a un nuevo repositorio en GitHub: [storelinkplatform](https://github.com/alvarowau/storelinkplatform).
