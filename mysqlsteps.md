#MYSQL COMMANDS
##STEP-1
*Entering to the server with login crential.
```
$baseservadmin
password:baseservADMIN
```
*Check and confirm IP adderss with following shell script.
```
$ifconfig
```
*If the server is install to Check status using following shell script.
```
$systemctl status mysql.service  -->ctrl+c
```
##STEP-2
###Setup mysql for remote access on ubutu server 16.04
*Open the port 3306 to access mysql remotely.
```
$sudo ufw allow in on eth1 to any port 3306
```
*Configure the mysql configuration to allow all IP address to send and receive request from remote server.
```
$sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
While setting mysql conf. to database for remote access change the ip address from '127.0.0.1' to wildcard (universal) address like '0.0.0.0',
then ** ctrl+x and enter->y **
*Restart and check status using following shell script
```
$systemctl restart mysql.service
```
```
$systemctl status mysql.service
```
##STEP-3
###Database Creation
*Sign into MySql with root user to create new database
```
$mysql -u root -p
password:baseservMYSQLADMIN
```
*Create database in mysql
```
mysql> create database dbname;
```
*View databases
```
mysql> show databases;
```
##STEP-4
###Create user and set privileges
*Create a new user
```
mysql> CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
*Set privileges to the user to create edit database
```
mysql> GRANT ALL ON dbname . * TO 'newuser'@'localhost' IDENTIFIED BY 'password';
```
*while setting privileges to database for remote access change the ip address from 'localhost' to wildcard address like '192.168.%.%'
```
mysql> GRANT ALL ON dbname . * TO 'newuser'@'192.168.%.%' IDENTIFIED BY 'password';
```
*Flush all privileges 
```
mysql> FLUSH PRIVILEGES;
```
*Finally close the root user
```
mysql> quit;
```
##STEP-5
###Table Creation
*Sign into MySql user to create new table
```
$mysql -u username -p
password:.......
```
*Select database
```
mysql> use dbname;
```
*create table
```
mysql>CREATE TABLE table_name(column_name column_type..);
```
*View tables
```
mysql>show tables;
```
*View table structure
```
mysql>DESC table_name;
```
