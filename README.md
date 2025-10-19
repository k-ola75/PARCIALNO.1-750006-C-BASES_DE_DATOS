# PARCIALNO.1-750006-C-BASES_DE_DATOS

# Base de Datos Servilimar

Este proyecto describe el despliegue de un entorno de base de datos PostgreSQL v14 junto con pgAdmin 4, usando contenedores Docker en Windows.
La base de datos `servilimar` está diseñada para el **sistema de generación de turnos LiMar**.

---

## Requisitos

Antes de iniciar es necesario:

- Conexión a Internet
- Instalar Docker Desktop (https://www.docker.com/products/docker-desktop/)
- Acceso a la terminal de Windows (CMD o PowerShell)
- Instalar WSL (https://learn.microsoft.com/es-es/windows/wsl/install)
---


## 1. Crear una red Docker

Permite la comunicación entre PostgreSQL y pgAdmin:
```
docker network create postgres-net
```

## 2. Desplegar contenedor de PostgreSQL 14
```
docker run -d --name contenedor --network postgres-net -e POSTGRES_USER=ulimar -e POSTGRES_PASSWORD=ex4men_db -p 5432:5432 postgres:14
```
Detalles
Usuario: ulimar
Contraseña: ex4men_db
Puerto expuesto: 5432

## 3. Desplegar contenedor de pgAdmin 4
```
docker run -d --name pgadmin4 --network postgres-net -e PGADMIN_DEFAULT_EMAIL=usuario@servilimar.com -e PGADMIN_DEFAULT_PASSWORD=limar#123 -p 5050:80 dpage/pgadmin4
```
Detalles:
Acceso web: http://localhost:5050
Usuario: usuario@servilimar.com
Contraseña: limar#123

## 4. Creación del servidor
Ingresar a: http://localhost:5050
Usuario: usuario@servilimar.com
Contraseña: limar#123

Clic en Add New Server.
En pestaña general: Nombrar el seridor.

En la pestaña connection:
Host name / address: contenedor (es el nombre del contenedor)
Port: 5432
Username: ulimar
Password: ex4men_db









