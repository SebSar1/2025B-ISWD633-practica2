## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
# COMPLETAR
```
docker network create red_ejercicio_4 -d bridge
```
### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
# COMPLETAR
```
docker run -d --name mysql-contenedor --network red -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=dbwp -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin mysql:8
```
### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
# COMPLETAR
```
docker run -d --name wordpress-contenedor --network red -p 8000:80 -e WORDPRESS_DB_HOST=mysql-contenedor:3306 -e WORDPRESS_DB_USER=admin -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=dbwp wordpress
```
De acuerdo con el trabajo realizado, en el esquema del ejercicio el puerto a es **(completar con el valor)**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
# COLOCAR UNA CAPTURA DE LA CONFIGURACIÓN
<img width="1908" height="1034" alt="image" src="https://github.com/user-attachments/assets/97591dba-dd85-4a59-837c-71595d19482e" />

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
# COLOCAR UNA CAPTURA DEL SITO EN DONDE SEA VISIBLE LA PUBLICACIÓN.
<img width="1906" height="1026" alt="image" src="https://github.com/user-attachments/assets/be541327-137c-4787-87a0-08db89ae360f" />
<img width="1906" height="1034" alt="image" src="https://github.com/user-attachments/assets/1326c075-ac2b-4ee1-b39e-ff16daeb9372" />

### Eliminar el contenedor wordpress
# COMPLETAR
```
docker rm -f contenedor-wordpress
```
### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

### ¿Qué ha sucedido, qué puede observar?
# COMPLETAR

