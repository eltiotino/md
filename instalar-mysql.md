hacemos todos los pasos de 

https://comoinstalar.me/como-instalar-mysql-8-en-ubuntu/

- wget https://dev.mysql.com/get/mysql-apt-config_0.8.16-1_all.deb
- sudo dpkg -i mysql-apt-config_0.8.16-1_all.deb
- sudo apt update
- sudo apt -y install mysql-server
- systemctl status mysql
- mysql -u root -p 



78

I know this an old Question but i feel this might help someone. I was recently faced with the same problem but in my case, i remember my password quite alright but it kept on giving me the same error. I tried so many solutions but still none helped then i tried this

mysql -u root -p 

after which it asks you for a pass word like this

Enter password: 

and then i typed in the password i used. That's all

#### para desintalar 

https://www.sololinux.es/desinstalar-mysql-server-en-ubuntu/


#### borrar instalación antigua

https://unix.stackexchange.com/questions/389747/error-processing-package-mysql-community-server-during-apt-get-upgrade

'''


you can purge all and reinstall

fisrt of all , do a backup of your usefull databse

to purge all do this

1- basic check of DBSM:

dpkg -l | grep -e mysql-server -e mariadb-server

do this lab

kill all mysql process

sudo service mysql stop 
sudo killall -9 mysql 
sudo killall -9 mysqld


sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-core-5.7 mysql-client-core-5.7  
            
sudo apt-get remove --purge mysql* 
sudo apt-get purge mysql*
sudo apt-get remove dbconfig-mysql 

sudo apt-get autoremove
sudo apt-get autoclean

remove mysql old files

sudo rm -rf /etc/mysql /var/lib/mysql
sudo rm -rf /var/lib/mysql
sudo rm -rf /etc/mysql

update

sudo apt-get dist-upgrade -y
sudo apt update

then reinstall

sudo apt-get install mysql-server and mysql-community-server

Share
Improve this answer
Follow
edited Mar 7 at 6:59 
'''
