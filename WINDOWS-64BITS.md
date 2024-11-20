**Proceso de Instalación de herramientas y proyecto con spring framework (WINDOWS 64 BITS)**

**Herramientas para desarrollo**

- PostgreSQL/ pgAdmin4
- Postman
- JDK 23
- Visual Studio Code

**Primer Paso**

ingresar a https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
seleccionamos Windows x86-64 con la version **17**

![foto17](windows-img/foto17.png)

**Segundo Paso**

una vez ya descargado el instalador se ejecuta y pregunta la ruta donde quiere instalar postgres

![foto1](windows-img/foto1.png)

**Tercer Paso**

Seleccionamos qué programas queremos descargar y seleccionamos todos, ya que el primero es el servidor, el segundo es la interfaz gráfica, el tercero es el instalador y el cuarto es un programa que funciona desde la consola.

![foto2](windows-img/foto2.png)

**Cuarto Paso**

Ingresar unas credenciales para poder ingresar a postgresql

![foto3](windows-img/foto3.png)

**Quinto Paso**

Dejamos el puerto por defecto de postgres 5432

![foto4](windows-img/foto4.png)

**Inicio de stack builder**

**SEXTO PASO**

seleccionamos postgresql y damos click a siguiente

![foto5](windows-img/foto5.png)

**SÉPTIMO PASO**

donde dice database drivers seleccionamos la opción jdbc y en el apartado de web development la que dice httpd 59-1

![foto6](windows-img/foto6.png)

**OCTAVO PASO**

dar click en siguiente hasta que finalice la instalación.
Una vez terminada la instalación ya tenemos postgresql y pgAdmin, la interfaz para ver las bases de datos de postgres.

**NOVENO PASO**

ingresamos a https://www.postman.com/downloads/ damos click en instalar para windows x64 e iniciamos sesión con nuestra cuenta de google

![foto7](windows-img/foto7.png)

**DÉCIMO PASO**

ingresamos a https://www.oracle.com/co/java/technologies/downloads/ y seleccionamos esta opcion

![foto8](windows-img/foto8.png)

**ONCEAVO PASO**

Damos click a next hasta finalizar la instalación

![foto9](windows-img/foto9.png)

**DOCEAVO PASO**

Ingresamos a https://code.visualstudio.com/ damos click en  instalar para windows.

![foto16](windows-img/foto16.png)

**TRECEAVO PASO**
Seleccionamos la ruta que deseemos y damos a siguiente.

![foto10](windows-img/foto10.png)

en los siguientes pop ups dejamos las opciones por defecto y le damos a instalar .

**CATORCEAVO PASO**

en abrimos visual studio code y seleccionamos este icono ubicado en la parte superior izquierda.

![foto11](windows-img/foto11.png)

y descargamos la siguiente extensión.

![foto12](windows-img/foto12.png)

Una vez tengamos ya descargadas estas tres herramientas nos vamos a dirigir a github a clonar el repositorio del proyecto con spring.

**QUINCEAVO PASO**

creamos una carpeta con el nombre que queramos y clonamos el repositorio de github.

![foto13](windows-img/foto13.png)

en la consola ejecutamos el comando git clone https://github.com/Petriv2004/Jugadores.git

**DIECISEISAVO PASO**

Abrimos el proyecto con visual studio code y entramos a la configuración del programa y ponemos nuestras credenciales en el archivo application.yaml ubicado en la carpeta resources del proyecto.

![foto14](windows-img/foto14.png)

veremos un archivo de configuración como este y en la parte de username y password ponemos las credenciales que pusimos para la base de datos en el instalador de postgres.

**DIECISIETEAVO PASO**

Nos dirigimos a la clase principal del proyecto que se llama jugadoresApplication.java y compilamos el programa y estaría listo para hacer las peticiones por postman.

**DIECIOCHOAVO PASO**

En la parte superior Izquierda especificamos el tipo de petición que vamos a hacer en este caso post, a la derecha ingresamos la url del backend con su cuerpo en formato json y con esta petición podemos agregar el jugador.

![foto15](windows-img/foto15.png)

**TODAS LAS PETICIONES**

**POST**

 - localhost:8080/campeonatos/add

{
  "nombre": "La Liga"
}

- localhost:8080/equipos/add
  
{
  "nombre": "R. Madrid"
}

**PUT**

- localhost:8080/jugador/1
  
{
  "nombre": "Juan Pérez",
  "edad": 20,
  "posicion": "Volante",
  "equipo": {
    "id": 2,
    "nombre": "City"  
  },
  "campeonatoList": [
    {
      "id": 1,
      "nombre": "Campeonato Nacional"
    },
    {
      "id": 2,
      "nombre": "La Lig"
    }
  ]
}

- localhost:8080/equipos/2

{
  "nombre": "M. City"
}

- localhost:8080/campeonatos/2

{
  "nombre": "La Liga"
}

**GET (SIN CUERPO)**

- localhost:8080/jugador/all localhost:8080/equipos/all 

- localhost:8080/campeonatos/all 

- localhost:8080/campeonatos/campeonatoJ/3

- localhost:8080/equipos/jugadoresT/3

- localhost:8080/jugador/orderbyName


**DELETE (SIN CUERPO)**

- localhost:8080/jugador/1
  
- localhost:8080/equipos/2
  
- localhost:8080/campeonatos/2

**RECUERDE QUE PARA INGRESAR UN JUGADOR DEBE EXISTIR PREVIAMENTE EL EQUIPO Y LA LIGA A LA QUE PERTENECE**


