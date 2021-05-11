
# Curso de Docker Compose 2

Partiemos de nuestro fichero
```
version: "3.8"
services: 
  nginx:
    image: nginx-alpine
    ports:
      - 8080:80
```
Vamos a cambiar el nombre al contenedor

```
version: "3.8"
services: 
  nginx:
    image: nginx-alpine
    container_name: tiotino
    ports:
      - 8080:80
```
a veces ecesitamos utilizar el archivo original
para ellos tenemos el Dockerfile Original

```
version: "3.8"
services: 
  nginx:
    build: 
      context: .
      dockerfile: Dockerfile
    image: nginx-alpine
    container_name: tiotino
    ports:
      - 8080:80
```
El archivo Dockerfile es:
```
FROM nginx:alpine
```

levantamos el servicio y vemos que esta levantado
```
docker-compose up -d
```
voy a modificar el dockerfile para que mande un mensaje
```
FROM nginx:alpine
RUN echo 'Hola Mundo'
```


para que se tome en cuenta los cambios he de realizar
```python
docker-compose up -d --build
```
Otras de las variables a tener en cuenta es los errores del contenedor

debemos incluir el inicio

las opciones son:
```

rstart:"no"
restart: always
restart: on-failure
restart: unless-stop
```
siempre incluimos la opcion restart: always

```
version: "3.8"
services: 
  nginx:
    build: 
      context: .
      dockerfile: Dockerfile
    image: nginx-alpine
    restart: always
    container_name: tiotino
    ports:
      - 8080:80
```
A veces queremos enviar informacion desde el contenedor mediante enviroment
Puedo poner los nombres que quiera

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
para ver la variable vamos a entrar al contenedor

```
docker exec -it 8888 /bin/sh
```

y puedo visualizar mi variable con:
```
echo $MYVARIABLE
```


