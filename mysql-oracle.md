# Mysql con Oracle

https://docs.oracle.com/en/java/java-components/advanced-management-console/2.21/install-guide/mysql-database-installation-and-configuration-advanced-management-console.html#GUID-2B24F7E4-A00C-463F-8666-10D3D1097061

- sudo yum install mysql-community-server
- sudo systemctl start mysqld

ver la password

- sudo grep 'A temporary password is generated for root@localhost' /var/log/mysqld.log |tail -1

- sudo mysql -u root -p 


