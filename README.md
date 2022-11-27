# Docker Proyecto final Ingenieria Web
## Documentacion
### Login cuenta de Azure
> ![Imagen login](https://github.com/Sespinosa11/Docker/blob/main/images/1.png)

### Creación de una instancia de Azure Container Registry
Para crear un grupo de recursos, use el comando az group create, cuando se haya creado el grupo de recursos, cree un registro de contenedor de Azure con el comando az acr create.
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/2.png)
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/3.png)
### Inicio de sesión en el registro de contenedor y obtención del código de la aplicación
Debe iniciar sesión en la instancia de Azure Container Registry antes de insertar imágenes en ella.
La aplicación de ejemplo que se usa en este tutorial es una aplicación básica para votar. La aplicación consta de un componente web front-end y de una instancia back-end de Redis. El componente web se empaqueta en una imagen de contenedor personalizada. La instancia de Redis usa una imagen sin modificar de Docker Hub. cambiar al directorio donde se clono, en el directorio se encuentra el código fuente de la aplicación, un archivo de Docker Compose creado previamente y un archivo docker-compose.yaml.
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/4.png)
### Modificación del archivo de Docker Compose
Abra el archivo docker-compose.yaml en un editor de texto. El archivo configura los servicios azure-vote-back y azure-vote-front.
En la configuración azure-vote-front, se realizan dos cambios los cuales son los siguientes:
1. Actualice la propiedad image en el servicio azure-vote-front. Use como prefijo, en el nombre de la imagen, el nombre del servidor de inicio de sesión del registro de contenedor, <acrName>.azurecr.io. Por ejemplo, si el registro se denomina myregistry, el nombre del servidor de inicio de sesión es myregistry.azurecr.io (todo en minúsculas) y la propiedad de imagen es myregistry.azurecr.io/azure-vote-front.
2. Cambie la asignación de ports a 80:80. Guarde el archivo.
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/5.png)
### Ejecución local de una aplicación de varios contenedores
Ejecute el archivo docker-compose up, que usa el archivo docker-compose.yaml para compilar la imagen de contenedor, descargue la imagen de Redis e inicie la aplicación:
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/6.png)
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/7.png)
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/8.png)
#### Cuando haya finalizado, use el comando docker images para ver las imágenes creadas. Se han descargado o creado tres imágenes. La imagen azure-vote-front contiene la aplicación de front-end y usa la imagen uwsgi-nginx-flask como base. La imagen redis se usa para iniciar una instancia de Redis.
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/9.png)
#### Ejecute el comando docker ps para ver los contenedores en ejecución:
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/10.png)
#### Para ver la aplicación en ejecución, escriba http://localhost:80 en un explorador web local. Se carga la aplicación de ejemplo, como se muestra en el ejemplo siguiente:
> ![Imagen localhost](https://github.com/Sespinosa11/Docker/blob/main/images/11.PNG)
#### Después de probar la aplicación local, ejecute docker-compose down para detener la aplicación y quitar los contenedores.
### Inserción de imágenes en Container Registry
> ![Imagen creacion](https://github.com/Sespinosa11/Docker/blob/main/images/12.png)
  


