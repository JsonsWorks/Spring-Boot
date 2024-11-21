**Introducción:**

Spring Boot es una extensión de Spring, este último es un Framework de desarrollo que permite crear aplicaciones empresariales robustas, escalables y seguras para Java, Kotlin y Groovy. Spring Boot simplifica aún más el desarrollo de aplicaciones al reducir la cantidad de configuración manual requerida y proporcionar características listas para usar.

Esto último quiere decir que por la naturaleza del Framework reduce la necesidad de configuración manual a través de convenciones y autoconfiguración que ayudan a que la programación sea mucho más fácil e intuitiva.

Otra de las razones por las cuales nos llama la atención este Framework es debido a que para el desarrollo de plataformas web es de los Frameworks más conocidos para el lenguaje que se nos enseña principalmente en la universidad, es decir, Java.

Algo importante a aclarar es que preferimos el uso de Spring Boot por encima del Spring ya que en Spring tradicional, necesitas configurar de forma explícita el contexto de aplicación y los beans, mientras que Spring Boot usa autoconfiguración.

A parte de utilizar Spring Boot, se utiliza Spring Data JPA (Java Persistence API) el cual es un ecosistema de Spring que proporciona una capa de abstracción para interactuar con bases de datos relacionales y no relacionales como lo puede ser en nuestro caso Postgresql. Una de las ventajas que ofrece este ecosistema es que el desarrollador se enfoca mucho más en la lógica de la base de datos antes que en la gestión manual de los datos, en donde para hacer CRUD hay que escribir menos código.

En esta presentación tenemos como propósito enseñar a utilizar tanto Spring Boot como Spring Data JPA para Java desde el editor de Intellij con la base de datos Postgresql con un ejemplo.

**Cifras:**  
Existen varias empresas que utilizan spring como framework tanto para construir servicios en su arquitectura microservicios, mejor escalabilidad, rendimiento y aplicaciones backend.   
Entre las empresas más famosas que lo utilizan son Netflix ($31.6 mil millones), Ebay ($9.8 mil millones), Alibaba ($125.5 mil millones), BMW ($132.2 mil millones), IBM ($60.5 mil millones) y entre otros.

**Comparativa:7**

Para haber decidido en conocer este framework lo comparamos con otros frameworks que sean útiles también para Java, de los cuales sacamos las siguientes conclusiones:

Java EE: Basado en especificaciones, contenedores de servlets, y componentes empresariales, su configuración puede ser extensa y engorrosa además de ser mucho menos popular y usada que Spring

Grails: Comparado con Spring, la documentación puede ser menos extensa.

Play Framework: La programación reactiva (paradigma de programación que se centra en la gestión de flujos de datos y la propagación de cambios) puede ser desafiante para quienes están acostumbrados a enfoques más tradicionales.

Micronaut: Muy joven y al igual que con Java EE carece de popularidad a comparación con Spring por lo que también tiene una comunidad pequeña.  
**Justificación:**

Por estas razones, popularidad, gran uso de otras empresas, facilidad, simplificación de código, y en general la convivencia es que elegimos este framework para aprender y presentar.

**![][image1]**  
Este es el modelado para realizar el ejemplo en la explicación.

**PETICIONES**

**API REST**

Rest (Representational State Transfer) es una arquitectura para APIs normalmente basada en la web que define un conjunto de restricciones para crear servicios web,  REST se utiliza principalmente para construir APIs en la web que permiten interactuar con aplicaciones a través del protocolo HTTP.

Los principios de REST son:

* Cliente-servidor: El cliente (por ejemplo, una aplicación frontend) solicita recursos al servidor, que los proporciona.  
* Sin estado (Stateless): Cada petición HTTP desde el cliente al servidor debe contener toda la información necesaria para que el servidor la procese. El servidor no almacena el estado de la sesión entre solicitudes.  
* Cacheable: Las respuestas deben ser cacheables (cuando sea apropiado), para mejorar el rendimiento.  
* Interfaz uniforme: Todas las interacciones entre cliente y servidor deben seguir una interfaz estándar. Normalmente, esto se basa en métodos HTTP como GET, POST, PUT, DELETE para interactuar con recursos.  
* Recursos: En REST, los elementos con los que se trabaja son representaciones de recursos, que suelen estar identificados por un URI (Uniform Resource Identifier), como /users, /orders, etc.  
* Representación de recursos: Los recursos se transfieren en representaciones como JSON, XML, HTML, etc.

**OTRAS APIS**

 API SOAP: (Simple Object Access Protocol), que es otra arquitectura popular para APIs web, utiliza el protocolo SOAP y XML para el intercambio de información. 

APIs locales: Como las APIs de un framework como `Swing` en Java, que proporciona componentes gráficos para crear interfaces de usuario.

**EJEMPLO**

1. Obtener todos los Jugadores:  
   * Método HTTP: `GET`  
   * URI: `/Jugadores`  
   * Respuesta: JSON con la lista de Jugadores.  
2. Crear una nueva publicación:  
   * Método HTTP: `POST`  
   * URI: `/Jugadores`  
   * Cuerpo: Un objeto JSON con los detalles del jugador inscrito.  
3. Actualizar un usuario:  
   * Método HTTP: `PUT`  
   * URI: `/Jugadores/1`  
   * Cuerpo: Un objeto JSON con los datos actualizados del Jugador.  
4. Eliminar una publicación:  
   * Método HTTP: `DELETE`  
   * URI: `/Jugador/5`  
   * Elimina la Jugador con ID `5`

**Servicios**

En Spring Boot, un servicio es una clase con lógica de negocio o funcionalidad específica que puede ser reutilizada en distintas partes de la aplicación. Los servicios son parte de la capa de servicio (o capa de lógica de negocio) y suelen interactuar con la capa de acceso a datos (repositorios) para realizar operaciones sobre la base de datos, aplicar reglas de negocio, o transformar datos antes de enviarlos a la capa de presentación o controlador.

Marcación con `@Service`: Los servicios en Spring Boot se definen con la anotación `@Service`, que indica que la clase es un componente de servicio gestionado por el contenedor de Spring.

![][image2]

Propósito Principal: Los servicios centralizan la lógica de negocio, manteniendo a los controladores más ligeros y enfocados en manejar las solicitudes y respuestas HTTP. La capa de servicio interactúa con los repositorios para realizar las operaciones necesarias y procesar datos.

**Configuración y dependencias:**

1. **Spring Boot Starters para manejar dependencias**  
   Los starters son paquetes que simplifican la carga de dependencias, para en vez de agregar cada dependencia de manera individual, los starters se encargan de agrupar las dependencias necesarias para cada funcionalidad. Esto facilita a que los proyectos comiencen rápidamente y se priorice la lógica con el objetivo de no preocuparse por la gestión de múltiples bibliotecas  
     
   Por ejemplo, el spring-boot-starter-web trae todo lo necesario para crear aplicaciones web: incluye dependencias como Spring MVC, Tomcat como servidor embebido y utilidades para construir APIs REST, también el spring-boot-starter-data-jpa, incluye JPA (Java Persistence API) y el conector de la base de datos H2.  
     
   Estos paquetes simplifican la gestión de dependencias, donde garantizan la compatibilidad entre versiones y reducen los errores y conflictos de versiones al venir preconfiguradas  
     
2. **Configuración del proyecto: application.properties y application.yaml**  
   Son archivos donde se configuran los aspectos claves del proyecto, tales como la conexión a la base de datos, configuraciones de correo para sus envíos, puertos, etc. Adicionalmente permiten centralizar la configuración del proyecto y posteriormente ajustar para diferentes entornos.  
- application.properties es un archivo cuya configuración es a partir de una sintaxis clave valor, siendo más utilizado en proyectos Java  
- application.yaml es un archivo cuya configuración está basada en un formato YAML, es decir, un archivo de configuración de sintaxis sencilla y legible cuya representación de datos está de forma jerárquica.

**¿Qué es JPA?**

JPA (Java Persistence API) es **una herramienta que facilita la interacción entre las aplicaciones Java y las bases de datos**.

### **Explicación Sencilla:**

* **Qué es JPA**: JPA es una especificación de Java que te permite trabajar con bases de datos usando objetos de Java en lugar de escribir consultas SQL complejas.  
* **Cómo Funciona**: Imagina que tienes una clase Java llamada `Jugador` con atributos como `nombre`, `edad`, etc. JPA te permite guardar objetos de esa clase directamente en la base de datos y también recuperarlos fácilmente.  
* **Ventajas**:  
  1. **Menos Código SQL**: En lugar de escribir muchas líneas de SQL, puedes trabajar con métodos y objetos de Java.  
  2. **Portabilidad**: JPA funciona con diferentes bases de datos (MySQL, PostgreSQL, Oracle, etc.) sin necesidad de cambiar tu código.  
  3. **Mantenimiento Simplificado**: Al usar JPA, el código es más limpio y más fácil de entender.

**¿Cómo conectar la base de datos con el archivo de Spring Boot?**  
![][image3]  
En la carpeta de resources al archivo que tiene el nombre de application.properties, le cambiamos el nombre a application.yaml, que es donde irán las configuraciones para conectar la base de datos. 

Lo cual contendrá este código:

\#\# YAML Template.  
\---  
spring:  
  datasource:  
    url: jdbc:postgresql://localhost:5432/ejemplo1 \-\> es la dirección de la base de datos PostgreSQL   
    username: postgres \-\> el nombre de usuario para conectarse a la base de datos  
    password: \-\> la contraseña para el usuario de la base de datos  
    driver-class-name: org.postgresql.Driver \-\> es el controlador JDBC de PostgreSQL que Spring Boot utiliza para conectarse a la base de datos.  
  jpa:  
    hibernate: \-\> se encarga de traducir las operaciones de objetos a instrucciones SQL, y viceversa  
      ddl-auto: update \-\> Hibernate actualizará automáticamente el esquema de la base de datos basado en las entidades de la aplicación  
    show-sql: true \-\> Hace que las consultas SQL generadas por Hibernate se muestran en la consola durante la ejecución del programa.  
    properties:  
      hibernate:  
        format\_sql: true \-\> Hace que las consultas SQL sean más legibles  
    database: postgresql \-\> indica que el tipo de base de datos es PostgreSQL  
    database-platform: org.hibernate.dialect.PostgreSQLDialect \-\> define el dialecto que Hibernate utilizará para generar SQL específico para PostgreSQL

Luego que ya saber cómo generar el archivo de SpringBoot, les voy a explicar como crear una base de datos, ejecuten estos comandos en la consola de linux:

sudo \-u postgres psql \-\> entrar a la consola de psql  
CREATE DATABASE mi\_base\_datos; \-\> crear la base de datos  
\\l \-\> ver que si se creó  
\\q \-\> salir de la revisión

Vamos a conectar la base de datos a nuestro archivo con SpringBoot:

Instalamos el plugin DB Navigator:   
![][image4]   ![][image5]

Acá podemos comprobar que la conexión con la base de datos es exitosa:

Ahora voy a explicar las entidades:  
Las entidades JPA son clases de Java que representan tablas en una base de datos relacional. Se utilizan para mapear objetos Java a tablas de bases de datos, lo que permite a los desarrolladores trabajar con datos relacionales utilizando objetos Java.

**Anotaciones principales de las entidades**  
\-@Entity: Marca la clase de java como una entidad JPA, lo que significa que será mapeada a una tabla en la clase en la base de datos.  
\-@Table: Es una anotación opcional, se puede usar para especificar el nombre de la tabla y otros detalles de la tabla en la base de datos.  
![][image6]  
Si no se tiene la anotación @Table la tabla será creada con el nombre de la clase.  
\-@Id: Marca el atributo como la clave primaria de la identidad.  
\-@GenerateValue Opcionalmente, se puede usar junto con la anotación @Id para especificar cómo se generará el valor de la clave primaria:

GenerationType.AUTO: Permite a JPA elegir la estrategia de generación de claves automáticamente según el proveedor de la base de datos. Es el valor predeterminado.

GenerationType.IDENTITY: Utiliza una columna de incremento automático de la base de datos. Este valor es ideal si estás usando bases de datos que soportan columnas auto-incrementales, como MySQL.

GenerationType.SEQUENCE: Usa secuencias de base de datos para generar el valor de la clave primaria. Esto es útil en bases de datos que tienen soporte para secuencias, como PostgreSQL y Oracle. Para utilizar esta estrategia, normalmente debes definir una secuencia en la base de datos y, opcionalmente, puedes especificar su nombre con la anotación @SequenceGenerator.

GenerationType.TABLE: Almacena el último valor de la clave en una tabla especial en la base de datos y usa este valor para generar claves únicas. Este enfoque es útil para bases de datos que no admiten incrementos automáticos o secuencias, pero puede tener un rendimiento inferior en comparación con otras estrategias.

\-@Column: Permite personalizar el mapeo entre el atributo de la clase y la columna en la tabla de la base de datos.  
 ![][image7]  
\-@Transient: Marca un atributo de la clase como no persistente, lo que significa que no se mapeará a una columna en la tabla de la base de datos.  
\-@Temporal: Se utiliza para indicar cómo se debe tratar una propiedad de tipo java.util.Date o java.util.Calendar cuando se mapea a una base de datos.  
![][image8]día, mes y año  
![][image9]hora, minutos y segundos  
![][image10]día, mes, año y hora, minutos y segundos

Las entidades se almacenan en la carpeta de models siguiendo el patrón de MVC.

Ahí se explican las entidades del ejemplo.

**Anotaciones para Relaciones entre Tablas**  
Desde las clases de modelo, se codifica, desde las entidades, las relaciones que se van a establecer las distintas tablas.  
@ManytoOne  
![][image11]  
Desde la clase jugador se crea una relación de Muchos a uno para muchos jugadores a un equipo.  
Se crea el atributo con la llave foránea llamado “equipo \_id” que pertenece a la entidad de Jugadores  
Instancia un equipo de tipo Equipo que demuestra que cada que se cree un Jugador habrá una instancia de un Equipo asociada a dicho jugador  
@OnetoMany  
![][image12]  
Relación de uno a muchos de la entidad de Equipo a Jugadores  
El primer atributo mappedBy le da la responsabilidad a la propiedad equipo de la Lista de Jugadores.  
El segundo atributo especifica cómo se comportará la cascada para la relación la cual puede ser de las siguientes tres maneras:

1. Persistencia (PERSIST)  
2. Eliminación (REMOVE): Si eliminas una entidad, todas las entidades relacionadas serán eliminadas igualmente   
3. Fusión (MERGE): Si actualizas una entidad, las relacionadas serán actualizadas igualmente (se utiliza para guardar datos)  
4. Refrescar (REFRESH): Si refrescas una entidad, las relacionadas serán actualizadas en la base de datos (se utiliza para la restauración de datos)  
5. Desvinculación (DETACH): Se refiere a desvinculación con la operación de quitar el contexto de persistencia a una entidad junto con sus relaciones. (desincronización con la base de datos )  
6. Todas (ALL): Son todos los anteriores comportamientos para la relación entre Equipo y Jugadores

Por último se crea una lista con instancias de tipo Jugador para muchos jugadores.  
@ManytoMany  
![][image13]  
Desde la entidad de Jugadores se establece la relación de muchos a muchos jugadores  
@JoinTable es la notación que se usa para definir la tabla intermedia y guardar los datos de ambas tablas.  
Se le da el nombre a la tabla, se especifican los atributos foráneos que se le dará a la tabla incluyendo jugador id y campeonato \_id uniendo las distintas columnas.  
Al igual que con  One to Many se crea una lista pero en este caso para campeonato.  
![][image14]  
También desde la tabla de campeonatos se agrega la notación ManyToMany con la diferencia que no se incluye la notación de Join Table puesto que esta ya se estableció en la entidad de jugador.

Para mirar las tablas creadas por la terminal, se hace:

sudo \-u postgres psql \-\> entrar a la consola de psql  
\\l  
\\c \-\> nombre\_base\_datos  
\\dt \-\> mostrar las tablas

**Repositorios**  
Un repositorio es un componente que actúa como puente entre la aplicación y la base de datos. Los repositorios en Spring Data JPA están diseñados para aprovechar las capacidades de JPA y facilitar las operaciones con la base de datos.

La interfaz JpaRepository\<T, ID\> extiende CrudRepository y PaginAndSortingRepository, lo que da acceso a una amplia gama de métodos predefinidos.

**Sintaxis del repositorio**  
Para crear un repositorio, solo se necesita definir una interfaz que extienda de JpaRepository. La interfaz pide dos parámetros:

\-T: La entidad sobre la que se va a realizar la persistencia  
\-ID: El tipo de dato de la clave primaria de la entidad.

La interfaz JpaRepository proporciona muchos métodos útiles para trabajar con entidades. Algunos de los más comunes son:

**Operaciones CRUD:**  
save(S entity): Guarda o actualiza una entidad en la base de datos.  
findById(ID id): Encuentra una entidad por su clave primaria.  
findAll(): Recupera todas las entidades del repositorio.  
delete(T entity): Elimina una entidad de la base de datos.  
deleteById(ID id): Elimina una entidad por su clave primaria.

**Paginación y Ordenación:**  
findAll(Sort sort): Encuentra todas las entidades y las ordena.

**Consulta personalizada**  
También se puede definir consultas personalizadas y más complejas utilizando la la anotación de @Query. 

Por ejemplo:  
@Query("SELECT j FROM Jugador j WHERE j.equipo.nombre \= :nombreEquipo") List\<Jugador\> findJugadoresByEquipoNombre(@Param("nombreEquipo") String nombreEquipo);

@Param("nombreEquipo"): Esta anotación vincula el parámetro de la consulta :nombreEquipo con el argumento que le pasas al método en tiempo de ejecución. Es decir, el valor del argumento nombreEquipo que le pases cuando llames al método será utilizado para reemplazar el parámetro :nombreEquipo en la consulta.

Los  “:” indica que se va a pasar un parámetro en tiempo de ejecución.

nativeQuery \= true: Indica que la consulta está escrita en SQL nativo y no en JPQL. Esto significa que la consulta interactúa directamente con las tablas de la base de datos en lugar de trabajar con las entidades de JPA.

1\. **Lombok**: Es una biblioteca que reduce el código repetitivo en Java, como getters, setters, toString, equals, y hashCode. Al agregar Lombok, puedes usar anotaciones como @Getter, @Setter, @ToString, @EqualsAndHashCode, y @AllArgsConstructor, entre otras, que Lombok procesará en tiempo de compilación para generar este código automáticamente.

2\. **Spring Web**: Esta dependencia incluye las herramientas necesarias para construir aplicaciones web, incluyendo aplicaciones RESTful. Al agregarla, obtienes soporte para el modelo de programación MVC (Modelo-Vista-Controlador) de Spring, que permite crear endpoints, gestionar solicitudes HTTP, y desarrollar APIs web.

3\. **Spring Data JPA**: Proporciona una implementación de JPA (Java Persistence API) de Spring, que facilita la interacción con bases de datos relacionales. Con esta dependencia, puedes crear repositorios para interactuar con tus entidades de base de datos de forma fácil y sin escribir mucho código SQL, ya que Spring Data JPA genera las consultas automáticamente a partir de los métodos definidos en tus interfaces de repositorio.

4\. **PostgreSQL Driver**: Es el controlador JDBC para la base de datos PostgreSQL. Necesitas este controlador para que tu aplicación Spring Boot pueda conectarse y comunicarse con una base de datos PostgreSQL, permitiéndote realizar operaciones CRUD (Crear, Leer, Actualizar, Borrar) en la base de datos.

Referencias  
[https://www.tutorialesprogramacionya.com/springbootya/detalleconcepto.php?punto=13\&codigo=14\&inicio=0](https://www.tutorialesprogramacionya.com/springbootya/detalleconcepto.php?punto=13&codigo=14&inicio=0)   
[https://programandoenjava.com/jparepository-en-spring-data/](https://programandoenjava.com/jparepository-en-spring-data/) 

