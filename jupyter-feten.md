
# Instalar Jupytr feten en toltema-jupyter

## para instalar jupyter-lab
```
sudo apt update
sudo apt upgrade #Provide Y/yes as input when prompted.
sudo apt install python3-pipsudo pip3 install jupyterlab
exit
```

This will install the jupyterlab on your machine. Reconnect to the machine via SSH and execute below set of commands.

```
sudo jupyter serverextension enable --py jupyterlab --sys-prefix
jupyter lab --ip 0.0.0.0 --port 8888 --no-browser
```

## Cambiar contraseña

Now open the web browser and put the URL as http://<<static ip of VM>>:8888. This will show the screen as below.

introducir el código y cambiar la contraseña


## para configurar el firewall

https://gianniceresa.com/2019/12/jupyter-sandbox-in-an-oracle-cloud-compute-instance/


