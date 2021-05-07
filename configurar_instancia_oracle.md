
# Intancia Oracle

### Como obtener vps para siempre oracle Cloud

- Creamos la instancia
- antes debemos de tener una llave publica
- elegimos ubuntu 18.04 como imagen
- copiamos la direccion estatica y entramos mediante ssh
- username= ubuntu
- ssh ubuntu@....
- sudo apt update && sudo apt upgrade
- sudo fallocate -l 1G /swapfile
- sudo dd if=/dev/zero of=/swapfile bs=1024 count=1048576
- sudo chmod 600 /swapfile
- sudo mkswap /swapfile
- sudo swapon /swapfile
- sudo nano /etc/fstab
- **Agregar lo siguiente** 
- /swapfile swap swap defaults 0 0

- sudo mount -a 
- sudo reboot
