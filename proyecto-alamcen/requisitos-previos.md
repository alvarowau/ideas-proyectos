## Requisitos Previos

Antes de comenzar con el desarrollo del proyecto, asegúrate de tener las siguientes herramientas instaladas y correctamente configuradas en tu entorno de desarrollo:

- **Java (JDK)**: OpenJDK 21 (Amazon Corretto)
  - Verificado con el comando: `java --version`
  - Ruta configurada en `JAVA_HOME`: `C:\Program Files\Amazon Corretto\jdk21.0.4_7`

- **Maven**: [Versión específica]
  - Verificado con el comando: `mvn -version`
  - Se utiliza para la gestión de dependencias y la construcción del proyecto.

- **Gradle**: [Versión específica]
  - Verificado con el comando: `gradle -version`
  - Alternativa a Maven, puede ser utilizado según la preferencia.

- **Docker**: Versión 26.1.1
  - Verificado con el comando: `docker --version`
  - Docker se utilizará para la contenedorización de servicios y bases de datos.

- **Docker Compose**: Versión v2.27.0
  - Verificado con el comando: `docker-compose --version`
  - Se utilizará para orquestar múltiples contenedores Docker.

- **Git**: Versión 2.45.1
  - Verificado con el comando: `git --version`
  - Herramienta de control de versiones para gestionar el código fuente del proyecto.

### Recomendaciones
- **IDE**: Se recomienda utilizar IntelliJ IDEA (Community o Ultimate) para el desarrollo de este proyecto, ya que ofrece un excelente soporte para Spring Boot y herramientas relacionadas.
- **Postman**: Opcionalmente, Postman puede ser útil para probar las APIs REST durante el desarrollo.
- **Node.js**: Si planeas integrar frontend o usar herramientas como Webpack, asegúrate de tener Node.js instalado.
