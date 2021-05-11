# Curso docker-compose 3

partimos del siguiente fichero
```
version: "3.8"
services: 
  nginx:
    build: 
      context: .
      dockerfile: Dockerfile
    image: nginx-alpine
    restart: always
    enviroment:
      MYVARIABLE: "este es un mensaje desde docker-compose"
    container_name: tiotino
    ports:
      - 8080:80
      
```
y con el siguiente Dockerfile
``
FROM nginx:alpine
ARG MYARGUMENTO="UN aRGUMENTO"
RUN echo " hola soy ${MYARGUMENTO}"

``
reinicio el docker-compose up -d --build
nos imprime el argumento

```
version: "3.8"
services: 
  nginx:
    build: 
      context: .
      dockerfile: Dockerfile
    image: nginx-alpine
    restart: always
    args:
      - MYARGUMENTO: "Soy un Argumento"
    enviroment:
      MYVARIABLE: "este es un mensaje desde docker-compose"
    container_name: tiotino
    ports:
      - 8080:80
      
```
si reinicio de nuevo
nos imprime el argumento del docker-compose
lo podemos utilizar para configuraciones

## Volumenes

Vamos a crear nuestra propia paguna html
Creamos un directorio html y un index.html que modifica el de nginx

vamos a integrarlo mediante
```
version: "3.8"
services: 
  nginx:
    build: 
      context: .
      dockerfile: Dockerfile
    image: nginx-alpine
    restart: always
    args:
      - MYARGUMENTO: "Soy un Argumento"
    enviroment:
      MYVARIABLE: "este es un mensaje desde docker-compose"
    container_name: tiotino
    ports:
      - 8080:80
    volumes:
      - ./html/:/usr/share/nginx/html
```
reiniciamos y visulizamos el localhost y voilá


