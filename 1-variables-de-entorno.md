# Variables de Entorno
### ¿Qué son las variables de entorno?
# COMPLETAR

Usualmente son una relación *clave:valor*, para el correcto funcionamiento de una aplicación. 

Estas variables existen en el entorno del sistema operativo y pueden ser accedidas por aplicaciones durante su ejecución, dependiendo de su nivel de seguridad.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

# COMPLETAR
```
docker run -d --name contenedor-ventorno -e username=sebas -e role=admin nginx:alpine
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
```
docker inspect contenedor-ventorno
```
<img width="977" height="228" alt="image" src="https://github.com/user-attachments/assets/396c9b45-93c7-4b6b-a9a3-5a27a92eda71" />

### Crear un contenedor con la imagen de mysql, mapear todos los puertos
# COMPLETAR

```
docker run -P --name contenedor-mysql mysql 
```

### ¿El contenedor se está ejecutando?
# COMPLETAR
No
```
docker ps -a
```

### Identificar el problema
# COMPLETAR
<img width="1213" height="290" alt="image" src="https://github.com/user-attachments/assets/8f7a88ed-7f99-4c38-ab7f-8c14564cf8ae" />

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

### Crear un contenedor con mysql, mapear todos los puertos y configurar las variables de entorno mediante un archivo
# COMPLETAR
```
docker run -d -P --name contenedor-mysql3 -e MYSQL_ROOT_PASSWORD=sebas mysql
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
```
docker exec -it contenedor-mysql3 bash
mysql -u root -p
```
<img width="753" height="1202" alt="image" src="https://github.com/user-attachments/assets/91ea1711-afa7-4a56-b5a8-b6fa4f9299c1" />

### ¿Qué bases de datos existen en el contenedor creado?
# COMPLETAR
 - information_schema 
 - mysql  
 - performance_schema  
 - sys 
