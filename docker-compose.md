# Curso de Docker-compose

todo archivo de docker-compose tiene 4 apartados

### version
### servicios
### volumes
### redes

vamos a hacer nuestro primer docker-compose

version: "3.8"
services: 
  nginx:
    image: nginx-alpine
    
   
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

