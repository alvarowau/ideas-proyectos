# Tecnologías y Herramientas para la Creación de Microservicios

## 1. Lenguaje de Programación
- **Java**: El lenguaje principal para desarrollar los microservicios, seleccionado por su robustez y soporte empresarial.
- **Framework**: Utilizaremos **Spring Boot** por su facilidad para construir microservicios y su integración con Spring Cloud.

## 2. Comunicación entre Microservicios
- **REST API**: Para la comunicación síncrona entre microservicios utilizando RESTful APIs.
- **Mensajería Asíncrona**: **RabbitMQ** o **Apache Kafka** para la comunicación asíncrona, útil para eventos como notificaciones y auditoría.
- **gRPC**: Consideraremos **gRPC** para comunicaciones que requieran alto rendimiento o tiempo real.

## 3. Persistencia de Datos
- **Bases de Datos Relacionales**: **PostgreSQL** para almacenar datos estructurados y transaccionales. Cada microservicio tendrá su propia base de datos.
- **Bases de Datos NoSQL**: **MongoDB** o **Redis** para microservicios que requieran almacenamiento flexible o de alta escala.

## 4. Despliegue y Orquestación
- **Docker**: Para empaquetar cada microservicio como un contenedor, facilitando la portabilidad.
- **Kubernetes**: Para la orquestación de contenedores, permitiendo el escalado y la gestión de despliegues en producción.

## 5. Seguridad
- **OAuth 2.0 / JWT**: Implementaremos autenticación y autorización utilizando **OAuth 2.0** y tokens **JWT**.
- **Spring Security**: El framework principal para manejar la seguridad a nivel de aplicación.

## 6. Pruebas y Calidad de Código
- **JUnit** y **Mockito**: Para pruebas unitarias y de integración.
- **Postman** o **Insomnia**: Para pruebas manuales de las APIs REST durante el desarrollo.
- **SonarQube**: Para análisis estático de código y asegurar la calidad.

## 7. Monitoreo y Logging
- **ELK Stack** (Elasticsearch, Logstash, Kibana): Para centralizar logs y realizar búsquedas avanzadas.
- **Prometheus** y **Grafana**: Para monitoreo y visualización de métricas en tiempo real.
- **Zipkin** o **Jaeger**: Para trazabilidad distribuida, crucial en un entorno de microservicios.

## 8. DevOps y CI/CD
- **Jenkins** o **GitLab CI/CD**: Para pipelines de integración continua y despliegue continuo.
- **Helm**: Para gestionar despliegues de aplicaciones en Kubernetes.

## 9. API Gateway
- **Spring Cloud Gateway** o **Kong**: Para manejar la entrada unificada a los microservicios, implementando enrutamiento, balanceo de carga, y control de acceso.

## 10. Documentación
- **Swagger**: Para generar y mantener la documentación de las APIs REST.
- **Asciidoctor**: Para la documentación técnica del sistema, además de los .md files.

## Asignación de Tecnologías a Microservicios

### Microservicio de Gestión de Usuarios
- **Spring Boot** para la API REST.
- **PostgreSQL** para almacenar los usuarios.
- **Spring Security** con **OAuth 2.0** y **JWT** para manejar la autenticación.

### Microservicio de Notificaciones
- **Spring Boot** para la lógica.
- **RabbitMQ** para la mensajería asíncrona.
- **MongoDB** para almacenar mensajes y notificaciones.

## Pasos Siguientes
1. **Definir la arquitectura detallada**: Desglosar responsabilidades específicas y definir cómo interactuarán entre los microservicios.
2. **Prototipos y Pruebas**: Crear prototipos de los microservicios más críticos para validar las decisiones tecnológicas.
3. **Configuración del Entorno de Desarrollo**: Establecer Docker, Kubernetes y otras herramientas en los entornos de desarrollo.
4. **Documentación y Roadmap**: Completar la documentación técnica y definir un roadmap de desarrollo para cada microservicio.
