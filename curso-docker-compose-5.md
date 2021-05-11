# Curso Docker-composed parte 5

Vamos ha hablar de redes

```
docker network ls
```
aqui tenemos los redes que se tienen en docker


```
NETWORK ID          NAME                   DRIVER              SCOPE
9611704e7d36        bridge                 bridge              local
fb5549263db1        darwinex_db_network    bridge              local
4600253dc3eb        darwinex_web_network   bridge              local
5bb248ec3657        host                   host                local
6afd82b23f02        none                   null                local
```
vemos estas redes

podemos inspeccionarlas con
```
docker network inspect fb55
```
esto nos sirve para comunicarnos entre contenedores

y ver que ip tienen cada contenedor asignado


