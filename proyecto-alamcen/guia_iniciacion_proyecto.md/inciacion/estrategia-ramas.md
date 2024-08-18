# Estrategia de Ramas en Git

Este documento describe la estrategia de ramas en Git para el proyecto `StoreLinkPlatform`. Incluye cuándo y cómo crear ramas para diferentes propósitos, siguiendo un flujo de trabajo estructurado.

## 1. Rama Principal (`main`)

- **Propósito**: La rama `main` contiene el código estable que está listo para producción. Siempre debe estar en un estado desplegable.
- **Uso**:
  - El código en `main` está completamente probado y aprobado para su lanzamiento.
  - Solo se fusiona en `main` desde ramas `release` o `hotfix`.

## 2. Rama de Desarrollo (`develop`)

- **Propósito**: La rama `develop` es la rama principal para el desarrollo en curso. Todas las nuevas funcionalidades y mejoras se integran aquí.
- **Uso**:
  - Crea nuevas ramas de funcionalidad desde `develop`.
  - Fusiona las funcionalidades completadas de vuelta en `develop`.
  - Cuando `develop` está estable y listo para su lanzamiento, crea una rama `release` desde ella.

## 3. Ramas de Funcionalidad (`feature/*`)

- **Propósito**: Las ramas `feature` se utilizan para desarrollar nuevas funcionalidades o mejoras específicas. Permiten trabajar en características sin afectar la estabilidad de `develop`.
- **Cuándo Crear**:
  - Crea una rama `feature` desde `develop` cuando comiences a trabajar en una nueva funcionalidad.
- **Uso**:
  - Trabaja en la funcionalidad dentro de la rama `feature`.
  - Una vez completada, fusiona la rama `feature` de vuelta en `develop`.
  - Nombra la rama siguiendo el patrón `feature/nombre-funcionalidad`.

## 4. Ramas de Release (`release/*`)

- **Propósito**: Las ramas `release` se utilizan para preparar una nueva versión del proyecto antes de fusionarla en `main`. Permiten realizar ajustes finales y pruebas.
- **Cuándo Crear**:
  - Crea una rama `release` desde `develop` cuando estés listo para preparar una versión para producción.
- **Uso**:
  - Realiza los ajustes finales en la rama `release`.
  - Fusiona la rama `release` en `main` y `develop` una vez que esté lista.
  - Nombra la rama siguiendo el patrón `release/version-x.y.z`.

## 5. Ramas de Hotfix (`hotfix/*`)

- **Propósito**: Las ramas `hotfix` se utilizan para realizar correcciones rápidas en el código de producción. Permiten solucionar problemas críticos sin interrumpir el desarrollo en curso.
- **Cuándo Crear**:
  - Crea una rama `hotfix` desde `main` cuando necesites corregir un error crítico en producción.
- **Uso**:
  - Realiza la corrección dentro de la rama `hotfix`.
  - Fusiona la rama `hotfix` en `main` y `develop` una vez que esté completada.
  - Nombra la rama siguiendo el patrón `hotfix/nombre-correcion`.
