

### Crear la instancia

https://docs.oracle.com/en/solutions/machine-learning-sandbox/configuring-your-system1.html#GUID-1B72D0BE-4C78-4624-B5DD-DC1479E4AC80

https://gianniceresa.com/2019/12/jupyter-sandbox-in-an-oracle-cloud-compute-instance/

https://medium.com/analytics-vidhya/setting-up-jupyter-lab-instance-on-google-cloud-platform-3a7acaa732b7

https://blogs.oracle.com/cloud-infrastructure/set-up-a-machine-learning-workbench-on-oracle-cloud-infrastructure



#### 



### Instalar Jupyter Lab

Generate a Jupyter Notebook configuration file.

jupyter notebook --generate-config

The configuration file is created in /home/ubuntu/.jupyter/jupyter_notebook_config.py, which is outside the environment. As a result, the configuration applies to every Jupyter Notebook instance, no matter which environment it is in.
Open the configuration file in a text editor such as nano or vi, and add the following lines to the beginning:

c = get_config()
c.NotebookApp.ip = '0.0.0.0'
c.NotebookApp.open_browser = False
c.NotebookApp.port = 8888

Add a password to Jupyter Notebook. When prompted, enter a suitably strong password. You can run this command any time that you want to change the password.

jupyter notebook password

## arrancar jupyter

jupyter lab --ip 0.0.0.0 --port 8888 --no-browser

Install a certificate for encrypted communications over HTTPS. To install a self-signed certificate:

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout jupyter-key.key -out jupyter-cert.pem

Start Jupyter Notebook.

jupyter notebook --certfile=jupyter-cert.pem --keyfile=jupyter-key.key
