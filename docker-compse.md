
# Crear docker-compose

- Descargar app

Los contenedores pasan a ser servicios

> por ej docker run  --name database -v mysql-data/:/var/lib/mysql p 3306:3306 -e MYSQL_USER=user -e MYSQL_PASSWRD=123456  -e MYSQL_ROOT_PASSWORD=123456 mysql5.7

Esto lo paso a un archivo YAML

Lo primero es que version vamos a utilizar, lo lógico es la 3


'''
version: '3'
services:
  appseed-app:
    restart: always
    env_file: .env
    build: .
    ports:
      - "5005:5005"
    networks:
      - db_network
      - web_network
  nginx:
    restart: always
    image: "nginx:latest"
    ports:
      - "85:85"
    volumes:
      - ./nginx:/etc/nginx/conf.d
    networks:
      - web_network
    depends_on: 
      - appseed-app
networks:
  db_network:
    driver: bridge
  web_network:
    driver: bridge
'''



