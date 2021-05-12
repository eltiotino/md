# Instalar Flask en una VM de Ubuntu

https://docs.oracle.com/es-ww/iaas/developer-tutorials/tutorials/flask-on-ubuntu/01oci-ubuntu-flask-summary.htm


hay que abrir los puertos del firewall

```
sudo firewall-cmd --permanent --zone=public --add-port=5000/tcp
sudo firewall-cmd --reload
```

hay un problema con el tipo de red
