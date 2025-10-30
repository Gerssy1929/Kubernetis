# Hello World Docker App

## Diferencia entre `docker run` vs `docker exec`

### `docker run`
- **CREA** un nuevo contenedor desde una imagen
- **INICIA** el proceso principal del contenedor
- Se usa por primera vez para lanzar la aplicación

### `docker exec`  
- **EJECUTA** comandos adicionales en un contenedor **YA EXISTENTE**
- El contenedor debe estar **corriendo previamente**
- Se usa para debugging, administración o tareas adicionales

## Ejemplo:

# Construir imagen
docker build -t upc/hello:v1 .

# Ejecutar y validar 
docker run -d -p 8080:8080 --name hello-app upc/hello:v1
curl http://localhost:8080

# Health Check con docker exec
docker exec -it hello-app sh
echo "ok" > /.health
cat /.health
exit

# Reemplazar "usuario" por tu usuario de Docker Hub
docker tag upc/hello:v1 usuario/upc-hello:v1
docker login
docker push usuario/upc-hello:v1

