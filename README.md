# Spring Boot Project Setup

Este repositorio proporciona una guía para instalar todo lo necesario para trabajar con proyectos de Spring Boot en **Windows** y **Linux**, junto con herramientas clave como PGAdmin y otros recursos útiles.

---
## Índice
1. [¿Qué es Spring Boot?](#qué-es-spring-boot)
   - [¿Para qué se utiliza?](#para-qué-se-utiliza)
   - [Características principales](#características-principales)
2. [Requisitos previos](#requisitos-previos)
3. [Instalación](#instalación)
   - [Instalación en Windows](#1-instalación-en-windows)
---
## ¿Qué es Spring Boot?

Spring Boot es un framework de código abierto basado en **Java** que facilita la creación de aplicaciones web y servicios RESTful. Es parte del ecosistema **Spring Framework** y está diseñado para simplificar el desarrollo de aplicaciones Java al reducir la configuración manual y promover buenas prácticas.

### ¿Para qué se utiliza?

Spring Boot es ampliamente utilizado para desarrollar:
- **APIs RESTful**.
- **Aplicaciones web** de back-end.
- **Microservicios** escalables.
- **Aplicaciones de línea de comandos**.

Gracias a su flexibilidad y facilidad de uso, es ideal tanto para principiantes como para desarrolladores avanzados que buscan construir aplicaciones rápidamente.

### Características principales

1. **Configuración automática (Auto-Configuration):** Reduce el tiempo y esfuerzo necesarios para configurar manualmente las dependencias y el entorno.
2. **Servidor integrado:** Permite ejecutar aplicaciones sin necesidad de configurar un servidor externo como Tomcat o Jetty.
3. **Manejo de dependencias:** Utiliza Maven o Gradle para gestionar las librerías necesarias de forma sencilla.
4. **Compatible con microservicios:** Proporciona herramientas que facilitan la creación de arquitecturas basadas en microservicios.
5. **Seguridad incorporada:** Soporte para autenticación y autorización mediante **Spring Security**.
6. **Escalabilidad:** Adecuado para proyectos pequeños y grandes.
7. **Rápida integración con bases de datos:** Soporte nativo para bases de datos como PostgreSQL, MySQL y H2.

---

## Requisitos previos

### General
- JDK 17 o superior.
- Maven (opcional si tu editor de código lo gestiona automáticamente).
- Editor de código (opcional):
  - [Visual Studio Code](https://code.visualstudio.com/)
  - [IntelliJ IDEA](https://www.jetbrains.com/idea/)
  - [NetBeans](https://netbeans.apache.org/)
  - [Eclipse](https://www.eclipse.org/)

---

## Instalación

### 1. Instalación en Windows

#### JDK (Java Development Kit)
1. Descarga el instalador de la página oficial de [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) o [Adoptium](https://adoptium.net/).
2. Sigue las instrucciones del instalador para configurar el **JAVA_HOME**.

#### PostgreSQL y PGAdmin
1. Descarga PostgreSQL desde [aquí](https://www.postgresql.org/download/windows/).
2. Durante la instalación, asegúrate de seleccionar **PGAdmin**.
3. Configura un usuario y contraseña para la base de datos.

---
