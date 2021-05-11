# Curso de Docker-compose

todo archivo de docker-compose tiene 4 apartados

>** version **
>** servicios**
>** volumes**
>** redes**

vamos a hacer nuestro primer docker-compose

>version: "3.8"
>services: 
>  nginx:
>    image: nginx-alpine
    
   
Con esto ya puedo crear mi primer comando

>>> docker compose up

ya he levantado el servicio

Otro comando es
>>> docker-compose ps
>>> 
ahi vemos nuestro servidor de nginx

el problema que tenemos es que se ejecuta el archivo en primer plano
con el comando siguiente se ejecuta en segundo plano

>>> docker compose up -d
>>> 
Con el seguiente detenemos eldocker-compose

> docker-compose down
> 

Ahora hacemospara entrar por un puerto al contenedor.

```
version: "3.8"
services: 
  nginx:
    image: nginx-alpine
    ports:
      - 8080:80
```
y ahora ejecutamos de nuevo el comando
```bash
docker compose up -d
```
y vemos los servicios
```
docker compose ps
```

y ya puedo verlo en el puerto 8080
```
localhost:8080
```


