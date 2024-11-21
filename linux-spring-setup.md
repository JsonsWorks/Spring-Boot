# Proceso de Instalación de Herramientas y Proyecto con Spring Framework (Linux)

## Herramientas para Desarrollo

- PostgreSQL/ pgAdmin4
- Postman
- Cualquier IDE de su preferencia, en nuestro caso IntelliJ IDEA

## Paso Opcional: Desinstalación de PostgreSQL Previo

Antes de comenzar, si tiene instalado postgres anteriormente, puede desinstalarlo con los siguientes comandos desde la terminal:

```bash
sudo systemctl stop postgresql
sudo apt remove --purge postgresql*
sudo rm -rf /etc/postgresql /var/lib/postgresql
sudo deluser postgres
sudo delgroup postgres
sudo apt autoremove
sudo apt clean
```

## Primer Paso: Instalación de PostgreSQL

Abra la terminal y ejecute los siguientes comandos:

```bash
sudo apt update
sudo apt-get -y install postgresql postgresql-contrib
```

### Ingreso al Servidor de Postgres

```bash
sudo su - postgres
psql
```

#### Creación de Usuario

```sql
create user Nombre-de-usuario with password 'Su-contraseña';
```

Si recibe la respuesta `CREATE ROLE`, su usuario fue creado correctamente. 

Dar permisos de superusuario:

```sql
alter user Nombre-de-usuario with superuser;
```

Si recibe la respuesta `ALTER ROLE`, los permisos fueron aplicados correctamente.

## Segundo Paso: Creación de Base de Datos

```sql
create database nombre-de-la-base-de-datos owner Nombre-de-usuario;
```

Para listar todas las bases de datos:
```
\l
```
![Listado](/linux-img/foto1.png)

Para salir:
```
\q
exit
```

## Tercer Paso: Instalación de pgAdmin4

```bash
sudo apt install curl
sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
sudo apt install pgadmin4
```

![Logo PgAdmin](/linux-img/foto2.png)

## Cuarto Paso: Instalación de Postman

```bash
sudo apt update
sudo apt install snapd
sudo snap install postman
```

![Logo Postman](/linux-img/foto3.png)

## Quinto Paso: Instalación de IntelliJ IDEA

```bash
sudo apt update
sudo apt install snapd
sudo snap install intellij-idea-community --classic
intellij-idea-community
```

![Logo IntelliJ](/linux-img/foto4.png)

## Séptimo Paso: Importar Proyecto de Ejemplo

```bash
git clone https://github.com/Petriv2004/Jugadores 
```

### Pasos en IntelliJ:

1. Abrir IntelliJ
   ![IntelliJ Inicio](/linux-img/foto5.png)

2. Abrir proyecto clonado
   ![Abrir Proyecto](/linux-img/foto6.png)

3. Añadir como Proyecto Maven
   ![Añadir Maven](/linux-img/foto7.png)

4. Marcar directorio Java como Sources Root
   ![Sources Root](/linux-img/foto8.png)

5. Configurar `application.yaml`
   ![Configuración YAML](/linux-img/foto9.png)
   ![Configuración Credenciales](/linux-img/foto10.png)

6. Ejecutar aplicación
   ![Ejecución Aplicación](/linux-img/foto11.png)

7. Verificar tablas en pgAdmin4
   ![Tablas en pgAdmin](/linux-img/foto12.png)

## Octavo Paso: Peticiones con Postman

### POST Requests

#### Campeonatos
```
localhost:8080/campeonatos/add
{
  "nombre": "La Liga"
}
```
![POST Campeonato](/linux-img/foto13.png)

#### Equipos
```
localhost:8080/equipos/add
{
  "nombre": "R. Madrid"
}
```
![POST Equipo](/linux-img/foto14.png)

### PUT Requests

#### Jugador
```
localhost:8080/jugador/1
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
```
![PUT Jugador](/linux-img/foto15.png)

#### Equipos y Campeonatos
```
localhost:8080/equipos/2
{
  "nombre": "M. City"
}

localhost:8080/campeonatos/2
{
  "nombre": "La Liga"
}
```
![PUT Equipo](/linux-img/foto16.png)
![PUT Campeonato](/linux-img/foto17.png)

### GET Requests (Sin Cuerpo)

- `localhost:8080/jugador/all`
- `localhost:8080/equipos/all`
- `localhost:8080/campeonatos/all`
- `localhost:8080/campeonatos/campeonatoJ/3`
- `localhost:8080/equipos/jugadoresT/3`
- `localhost:8080/jugador/orderbyName`

### DELETE Requests (Sin Cuerpo)

- `localhost:8080/jugador/1`
- `localhost:8080/equipos/2`
- `localhost:8080/campeonatos/2`

**RECUERDE**: Para ingresar un jugador, debe existir previamente el equipo y la liga a la que pertenece.
