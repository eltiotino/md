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
