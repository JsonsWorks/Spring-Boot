# Spring Boot Project Setup

Este repositorio proporciona una guía para instalar todo lo necesario para trabajar con proyectos de Spring Boot en **Windows** y **Linux**, junto con herramientas clave como PGAdmin y otros recursos útiles.

---
## Índice
1. [¿Qué es Spring Boot?](#qué-es-spring-boot)
   - [¿Para qué se utiliza?](#para-qué-se-utiliza)
   - [Características principales](#características-principales)
2. [Introducción](#introducción)
3. [Comparativa de frameworks](#comparativa-de-frameworks)
4. [Requisitos previos](#requisitos-previos)
5. [Instalación](#instalación)
   - [Instalación en Windows](#1-instalación-en-windows)
   - [Instalación en Linux](#2-instalación-en-linux-debianubuntu)
6. [Spring Initializr](#spring-initializr)
7. [Probar el entorno](#probar-el-entorno)
8. [API REST y peticiones](#api-rest-y-peticiones)
9. [Servicios y repositorios](#servicios-y-repositorios)

---
# MiProyecto

Este proyecto utiliza recursos adicionales que puedes encontrar en el siguiente repositorio:

- [Jugadores](https://github.com/Petriv2004/Jugadores)

## ¿Qué es Spring Boot?

Spring Boot es un framework de código abierto basado en **Java** que simplifica el desarrollo de aplicaciones web y servicios RESTful. Es parte del ecosistema **Spring Framework** y está diseñado para reducir la configuración manual y promover buenas prácticas.

### ¿Para qué se utiliza?

Spring Boot es ampliamente utilizado para desarrollar:
- **APIs RESTful**.
- **Aplicaciones web** de back-end.
- **Microservicios** escalables.
- **Aplicaciones de línea de comandos**.

### Características principales

1. **Configuración automática:** Reduce el tiempo necesario para configurar dependencias y entornos.
2. **Servidor integrado:** Permite ejecutar aplicaciones sin configurar un servidor externo como Tomcat o Jetty.
3. **Manejo de dependencias:** Utiliza Maven o Gradle para gestionar librerías.
4. **Compatible con microservicios:** Ofrece herramientas para crear arquitecturas basadas en microservicios.
5. **Integración con bases de datos:** Soporte nativo para bases de datos como PostgreSQL y H2.

---
## Introducción

Spring Boot es una extensión de Spring, que permite crear aplicaciones empresariales robustas, escalables y seguras para Java, Kotlin y Groovy. Su naturaleza de autoconfiguración lo hace más fácil de usar que el Spring tradicional.

Además, el ecosistema **Spring Data JPA** simplifica la interacción con bases de datos relacionales, permitiendo al desarrollador centrarse en la lógica del negocio.

---
## Comparativa de frameworks

Se eligió Spring Boot frente a otros frameworks populares para Java debido a su:

1. **Popularidad:** Utilizado por empresas como Netflix, eBay y Alibaba.
2. **Facilidad de uso:** Menos configuración y más enfoque en el desarrollo.
3. **Documentación extensa:** Comparado con Grails y Play Framework.
4. **Comunidad:** Mayor que Micronaut y Java EE.

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
## Spring Initializr

[Spring Initializr](https://start.spring.io/) es una herramienta web que permite generar proyectos Spring Boot personalizados. Facilita la configuración inicial de tu proyecto y la selección de dependencias necesarias.

### ¿Cómo usarlo?

1. Accede a [Spring Initializr](https://start.spring.io/).
2. Configura tu proyecto con los siguientes parámetros:
   - **Project:** Maven o Gradle.
   - **Language:** Java.
   - **Spring Boot Version:** Elige una versión estable (recomendado: 2.7.x o superior).
   - **Group:** Tu nombre de paquete base (por ejemplo, `com.ejemplo`).
   - **Artifact:** El nombre del proyecto.
   - **Dependencies:** Selecciona las dependencias necesarias, como:
     - Spring Web (para crear APIs RESTful).
     - Spring Data JPA (para integración con bases de datos).
     - PostgreSQL Driver (para conectar con PostgreSQL).
     - Spring Boot DevTools (para recarga automática durante el desarrollo).
3. Haz clic en **Generate** y descarga el archivo ZIP.
4. Extrae el archivo y ábrelo en tu editor de código preferido.
---
## Probar el entorno

1. Clona este repositorio:
```bash
git clone 
```
2. Importa el proyecto generado desde Spring Initializr en tu editor.
Configura la base de datos PostgreSQL en el archivo application.properties o application.yaml
```bash
spring.datasource.url=jdbc:postgresql://localhost:5432/tu_base_datos
spring.datasource.username=postgres
spring.datasource.password=tu-contraseña
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

```
4. Ejecuta el proyecto en tu editor y verifica que funcione correctamente.
---

## API REST y peticiones

En Spring Boot, puedes construir APIs RESTful para interactuar con tu aplicación mediante el protocolo HTTP. Aquí tienes un ejemplo de las operaciones CRUD para una entidad `Jugador`:

1. **Obtener todos los jugadores:**
   - **Método HTTP:** `GET`
   - **Endpoint:** `/jugadores`
   - **Descripción:** Devuelve una lista de todos los jugadores.
   - **Ejemplo de respuesta:**
     ```json
     [
       {
         "id": 1,
         "nombre": "Luis",
         "equipo": "Equipo A"
       },
       {
         "id": 2,
         "nombre": "Ana",
         "equipo": "Equipo B"
       }
     ]
     ```

2. **Crear un jugador:**
   - **Método HTTP:** `POST`
   - **Endpoint:** `/jugadores`
   - **Descripción:** Crea un nuevo jugador.
   - **Cuerpo de la solicitud:**
     ```json
     {
       "nombre": "Carlos",
       "equipo": "Equipo C"
     }
     ```

3. **Actualizar un jugador:**
   - **Método HTTP:** `PUT`
   - **Endpoint:** `/jugadores/{id}`
   - **Descripción:** Actualiza un jugador existente por su ID.
   - **Cuerpo de la solicitud:**
     ```json
     {
       "nombre": "Carlos Gómez",
       "equipo": "Equipo C"
     }
     ```

4. **Eliminar un jugador:**
   - **Método HTTP:** `DELETE`
   - **Endpoint:** `/jugadores/{id}`
   - **Descripción:** Elimina un jugador existente por su ID.

---

## Servicios y repositorios

### Servicios

Los servicios en Spring Boot gestionan la lógica del negocio y permiten mantener los controladores más ligeros. Se definen con la anotación `@Service`.

**Ejemplo de servicio:**
```java
@Service
public class JugadorService {
    private final JugadorRepository jugadorRepository;

    public JugadorService(JugadorRepository jugadorRepository) {
        this.jugadorRepository = jugadorRepository;
    }

    public List<Jugador> obtenerJugadores() {
        return jugadorRepository.findAll();
    }

    public Jugador guardarJugador(Jugador jugador) {
        return jugadorRepository.save(jugador);
    }
}
```
---

## Repositorios

En Spring Boot, los repositorios son componentes que permiten la interacción directa con la base de datos. Se implementan utilizando Spring Data JPA y se definen como interfaces que extienden `JpaRepository`.

### Ejemplo de repositorio

```java
@Repository
public interface JugadorRepository extends JpaRepository<Jugador, Long> {
    // Consulta personalizada: Buscar jugadores por el nombre de su equipo
    List<Jugador> findByEquipoNombre(String nombreEquipo);
}
```
## Métodos comunes en `JpaRepository`

Spring Data JPA proporciona una interfaz rica con métodos predefinidos que simplifican la interacción con la base de datos.

### Operaciones CRUD

1. **Guardar o actualizar una entidad:**
```java
T save(S entity);
```
Ejemplo:
```java
Jugador jugador = new Jugador("Luis", "Equipo A");
jugadorRepository.save(jugador);
```
2. **Encontrar una entidad por su ID:**
```java
Optional<T> findById(ID id);
```
Ejemplo:
```java
Optional<Jugador> jugador = jugadorRepository.findById(1L);
jugador.ifPresent(System.out::println);
```
3. **Eliminar una entidad específica:**
```java
void delete(T entity);
```
4. **Eliminar por ID:**
```java
void deleteById(ID id);
```
5. **Obtener todas las entidades:**
```java
List<T> findAll();
```
Ejemplo:
```java
List<Jugador> jugadores = jugadorRepository.findAll();
jugadores.forEach(System.out::println);
```
