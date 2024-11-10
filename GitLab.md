Contenedor GitLab
====
Aquí explica el proceso de crear un contenedor con GitLab

 1. Crear un archivo Dockerfile:

El archivo Dockerfile define cómo se debe construir el contenedor. Este archivo debe estar en la raíz de tu repositorio. Ejemplo básico de un Dockerfile:

 Usa una imagen base (por ejemplo, Node.js)
FROM node:14

 Define el directorio de trabajo dentro del contenedor
WORKDIR /app

 Copia los archivos de tu aplicación al contenedor
COPY . .

 Instala las dependencias
RUN npm install

 Expone el puerto donde corre la aplicación
EXPOSE 3000

 Define el comando para correr la aplicación
CMD ["npm", "start"]

2. Configurar GitHub Actions:

Utilizaremos GitHub Actions para automatizar la construcción del contenedor. Esto se hace creando un archivo de flujo de trabajo dentro del repositorio.

   Crear un archivo de flujo de trabajo: En tu repositorio, crea el siguiente archivo de flujo de trabajo en el directorio .github/workflows/:

mkdir -p .github/workflows
touch .github/workflows/docker-image.yml

Escribir el flujo de trabajo: Edita el archivo .github/workflows/docker-image.yml y agrega lo siguiente para construir y publicar tu contenedor en Docker Hub (o cualquier otro registro):

   name: Build and Push Docker Image

   on:
   push:
   branches:
          - main  # Se ejecuta al hacer un push en la rama 'main'

   jobs:
   build:
   runs-on: ubuntu-latest

   steps:
        - name: Check out code
        - uses: actions/checkout@v2

        - name: Set up Docker Buildx
        - uses: docker/setup-buildx-action@v2

        - name: Cache Docker layers
        - uses: actions/cache@v2
        - with:
           - path: /tmp/.buildx-cache
           -  key: ${{ runner.os }}-buildx-${{ github.sha }}
           - restore-keys: |
              - ${{ runner.os }}-buildx-

        - name: Log in to Docker Hub
        -  uses: docker/login-action@v2
        -  with:
           - username: ${{ secrets.DOCKER_USERNAME }}
           - password: ${{ secrets.DOCKER_PASSWORD }}

        - name: Build and push Docker image
         - uses: docker/build-push-action@v3
         - with:
          - context: .
          - file: ./Dockerfile
          - push: true
          - tags: username/repository:latest  # Reemplaza con tu nombre de usuario y repositorio en Docker Hub

    - En este archivo:
   Se usa el docker/setup-buildx-action para habilitar la construcción avanzada de contenedores.
   Se define una cache para optimizar las construcciones futuras.
   El paso docker/login-action te permite autenticarte con Docker Hub usando tus credenciales (las cuales deberías agregar a los secretos del repositorio).
   Finalmente, docker/build-push-action construye y publica la imagen.

3. Configurar Secretos de GitHub:

Para que el flujo de trabajo pueda acceder a tu cuenta de Docker Hub, debes agregar tus credenciales como secretos en GitHub:

   Ve a tu repositorio en GitHub.
   Dirígete a Settings > Secrets and variables > Actions.
   Haz clic en New repository secret y agrega tus credenciales:
    - DOCKER_USERNAME: tu nombre de usuario en Docker Hub.
    - DOCKER_PASSWORD: tu contraseña de Docker Hub (o un token de acceso).

4. Hacer un Push al Repositorio:

Una vez que todo esté configurado, haz un push de tu código (incluido el Dockerfile y el flujo de trabajo) al repositorio de GitHub. GitHub Actions se ejecutará automáticamente cuando realices un push a la rama configurada (main en el ejemplo).
5. Verificar la construcción y publicación:

   Puedes ver el progreso de la construcción en la pestaña Actions de tu repositorio en GitHub.
   Si todo va bien, el contenedor se publicará en Docker Hub bajo la etiqueta latest.

6. Probar el contenedor:

Después de que el contenedor haya sido publicado, puedes descargarlo y probarlo usando Docker:

docker pull username/repository:latest
docker run -p 3000:3000 username/repository:latest

¡Y eso es todo! Has creado y publicado un contenedor automáticamente usando GitHub Actions. Este flujo de trabajo te permitirá construir y desplegar tu contenedor cada vez que realices un cambio en tu repositorio.
