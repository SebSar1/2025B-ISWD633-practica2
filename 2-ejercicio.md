### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:15-alpine3.21
NO ES NECESARIO, PERO SI SEGURO: Hay que crear una red, para hacer esto posible, porque es para permitir la comunicación interna y segura entre los contenedores Postgres y pgAdmin, evitando la exposición de puertos al host y habilitando la resolución por nombre de contenedor dentro del entorno aislado.
```
docker network create red_postgres
```

# COMPLETAR
```
docker run -d --name contenedor-postgres --network red_postgres -e POSTGRES_PASSWORD=sebas postgres:15-alpine3.21
```

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

# COMPLETAR
```
docker run -d --name cliente-postgres --network red_postgres -e "PGADMIN_DEFAULT_EMAIL=admin@admin.com" -e "PGADMIN_DEFAULT_PASSWORD=admin" -p 8080:80 dpage/pgadmin4
```
La figura presenta el esquema creado en donde los puertos son:
- a: 8080
- b: 80
- c: 5432
  
![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
# COMPLETAR CON UNA CAPTURA DEL LOGIN
<img width="1909" height="1015" alt="image" src="https://github.com/user-attachments/assets/64f4dd18-6227-4c39-900c-2cdaaf3ea705" />

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
<img width="901" height="598" alt="image" src="https://github.com/user-attachments/assets/2de62ea1-f1fa-49df-bc2b-0146004bc380" />

<img width="746" height="536" alt="image" src="https://github.com/user-attachments/assets/9d697db1-b9fe-4931-816d-50b11c6df3d1" />

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
```
docker exec -it contenedor-postgres bash
```

```
psql -U postgres -d info
```
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
<img width="640" height="412" alt="image" src="https://github.com/user-attachments/assets/6f17353a-3aef-47f3-afd6-91ca14388ee7" />

