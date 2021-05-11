# Parte 4 de curso de Docker-compose

Vamos a ver firmar nuestros volumenes como services
```
Partimos del siguiente .yml
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
ahora vamos a conformar el volumen del servicio
```
Partimos del siguiente .yml
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
volumes:
  html: {}
```
ahora vamos con

## Comandos

los podemos incluir en Dockerfile o en docker-compose

```
FROM nginx:alpine
ARG MYARGUMENTO="UN aRGUMENTO"
RUN echo " hola soy ${MYARGUMENTO}"

```
y le incluyo comandos
```
FROM nginx:alpine
ARG MYARGUMENTO="UN aRGUMENTO"
RUN echo " hola soy ${MYARGUMENTO}"
CMD ["echo", "mensaje creado desde docker"]
```
reinicializamos y podemos ver el mensaje
pero no en pantalla sino en el contenedor
```
docker-compose logs -f
```
y vemos el mensaje

podemos ver los servicios, vemos que se estaba reinicializando e imprimiendo el mensaje varias veces.

si queremos quitar el error quitamos los del CMD

### Ahora los hacemos desde el docker-compose
modificamos el docker-compose
```
Partimos del siguiente .yml
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
    command: ['echo', 'hola mundo de nuevo']
    container_name: tiotino
    ports:
      - 8080:80
    volumes:
      - ./html/:/usr/share/nginx/html
volumes:
  html: {}
```
reiniciamos y ejecutamos
ocurre el mismo error
y vemos el log ``docker-compose logs -f ``
detenemos el compose
si quitamos el command funciona perfectamente


