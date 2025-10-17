# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

Al comparar mis conocimientos antes y después de la práctica, logré mejorar mi manejoi de docker, pasando de la gestión básica de contenedores a la configuración de redes y variables de entorno:

### 1. Comandos Esenciales
### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```
* **¿Qué aprendí?**
  Que las variables de entorno son:
Usualmente son una relación clave:valor, para el correcto funcionamiento de una aplicación.
Estas variables existen en el entorno del sistema operativo y pueden ser accedidas por aplicaciones durante su ejecución, dependiendo de su nivel de seguridad.

Que las redes en ciertos casos: NO ES NECESARIO, PERO SI SEGURO: Hay que crear una red, para hacer esto posible, porque es para permitir la comunicación interna y segura entre los contenedores , evitando la exposición de puertos al host y habilitando la resolución por nombre de contenedor dentro del entorno aislado.


Consultar: Cómo se gestionan datos confidenciales con los secretos de Docker (Docker Secrets).
# Gestión de datos confidenciales con Docker Secrets

## ¿Qué son los secretos de Docker?

Docker Secrets es una funcionalidad diseñada para almacenar y gestionar datos confidenciales (como contraseñas, claves API, certificados o tokens) de forma segura dentro de un entorno Docker, especialmente cuando se usa Docker Swarm.

## Características principales

- Los secretos no se almacenan en texto plano dentro de las imágenes o contenedores.
- Se cifran en tránsito y en reposo dentro del clúster.
- Solo los servicios autorizados pueden acceder a los secretos que necesitan.
- No se exponen mediante variables de entorno, sino como archivos temporales dentro del contenedor.

## Cómo se crean y usan los secretos

### 1. Crear un secreto
```
echo "mi_clave_super_secreta" | docker secret create mi_secreto -
```

### 2. Listar los secretos existentes
```
docker secret ls
```

### 3. Usar el secreto en un servicio
```
docker service create   --name mi_servicio   --secret mi_secreto   nginx
```

### 4. Acceder al secreto dentro del contenedor
Dentro del contenedor, el secreto se monta en:
```
/run/secrets/mi_secreto
```
Puedes leerlo como un archivo normal:
```
cat /run/secrets/mi_secreto
```

## Buenas prácticas

- No incluir secretos en imágenes o repositorios de código.
- Rotar los secretos regularmente.
- Limitar el acceso solo a los servicios que los necesiten.
- Usar nombres descriptivos y versionado de secretos cuando sea necesario.

## Ejemplo práctico
```
# Crear el secreto
echo "claveBD123" | docker secret create db_password -

# Crear el servicio que lo usa
docker service create   --name app_con_secreto   --secret db_password   myapp:latest
```
Dentro del contenedor, la aplicación podrá leer la contraseña desde:
```
/run/secrets/db_password
```

> **Fuente:** ChatGPT (GPT-5), OpenAI, 2025.
