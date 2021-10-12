# Instalar wordpress


```
sudo apt update && sudo apt upgrade

sudo fallocate -l 1G /swapfile

sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576

sudo chmod 600 /swapfile

sudo mkswap /swapfile

sudo swapon /swapfile

sudo nano /etc/fstab
```
**Agregar lo siguiente al fstab**

```
/swapfile swap swap defaults 0 0
```
```
sudo mount -a

sudo reboot
```

# Configuramos el firewall

```
sudo apt-get install firewalld

sudo systemctl enable firewalld
sudo systemctl start firewalld

sudo firewall-cmd --state
sudo ufw disable


sudo firewall-cmd --list-all
sudo firewall-cmd --zone=public --permanent --add-port=80/tcp
sudo firewall-cmd --reload

```
# Instalamos apache

```
sudo apt -y install apache2
sudo systemctl restart apache2

```
vemos si se ve la página de inicio de apache en la ip de la maquina

# Instalamos PHP

```
sudo apt -y install php
sudo apt -y install php-mysql php-curl php-gd php-zipsudo chmod -R g+rw /var/www/html
php -v
sudo systemctl restart apache2
sudo nano /var/www/html/info.php

```


en nano incluimos la siguiente
```
<?php
phpinfo();
?>
```

si vamos a la direccion ip y tecleamos
Connect to **http://<your-public-ip-address>/info.php**.
  
veremos si está correcto.
  
# Configurar Apache Directorio
  
```
  sudo adduser $USER www-data
 ww-data:www-data /var/www/html
  sudo chmod -R g+rw /var/www/html
  ```
# instalar mysql

```
  sudo apt -y install mysql-server
  sudo mysql_secure_installation
  
  
  ```
  
seleccionamos el nivel de password y la password

  
# Establecer contraseña root

Para establecer la contraseña vamos a usar el comando mysqladmin. Debemos poner la contraseña entre comillas.
```

sudo mysqladmin --user=root password “[USER_PASSWORD]”
```
Verificar contraseña root

Verificaremos que a partir de ahora no se pueder acceder a MySQL sin contraseña.
```
sudo mysql
```
Como ven, no nos deja acceder. Así que utilizaremos la contraseña que acabamos de establecer.
```
sudo mysql -p -u root
```

  
