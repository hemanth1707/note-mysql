# 1.Setup mysql for remote access on ubutu server 16.04

#### First open the port 3306 to access mysql remotely

```
$sudo ufw allow in on eth1 to any port 3306
```

#### Second configure the mysql configuration to allow all IP address to send and receive request from remote server

```
$sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```

#### While setting mysql conf. to database for remote access change the ip address from '127.0.0.1' to wildcard \(universal\) address like '0.0.0.0'

Use this link to know more  [https://www.techrepublic.com/article/how-to-set-up-mysql-for-remote-access-on-ubuntu-server-16-04/](https://www.techrepublic.com/article/how-to-set-up-mysql-for-remote-access-on-ubuntu-server-16-04/)

Another one is [https://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](https://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html)

## 2.Set privillage to the user to create edit database

```
mysql> GRANT ALL PRIVILEGES ON dbname . * TO 'newuser'@'localhost' IDENTIFIED BY 'password';
```

#### while setting privilage to database for remote access change the ip address from 'localhost' to wildcard address like '192.168.0.%'

### step-1

Entering to the server with login crential.

Login

```
$baseservadmin
password:baseservADMIN
```

### step-2

Check and confirm IP adderss with following shell script

```
$ifconfig
```

### step-3

If the server is install to Check status using following shell script

```
$systemctl status mysql.service  -->ctrl+c
$sudo ufw status
```

## 3.Open port in **UFW**

Enable

```
$sudo ufw enable
```

Connect to a specific network interface

```
$sudo ufw allow in on eth1 to any port 3306
```

or use the following

```
$sudo ufw allow 3306/tcp
```

Restart

```
$sudo service ufw restart
```

Status

```
$sudo ufw status
```

To refer this link [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-16-04)

## 4.**DataBase**

Sign into MySql with root user to create new database

```
mysql -u root -p
password:baseservMYSQLADMIN
```

Create database in mysql

```
mysql> create database dbname;
```

View database

```
mysql> show databases;
```

Change database

```
mysql> select database();
mysql> use dbname;
```

Delete database

```
mysql> drop database dbname;
```

To refer this link [https://www.digitalocean.com/community/tutorials/how-to-create-and-manage-databases-in-mysql-and-mariadb-on-a-cloud-server](https://www.digitalocean.com/community/tutorials/how-to-create-and-manage-databases-in-mysql-and-mariadb-on-a-cloud-server)

## 5.**Create a new user**

```
mysql> CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```

```
mysql> GRANT ALL PRIVILEGES ON dbname . * TO 'newuser'@'localhost' IDENTIFIED BY 'password';
```

```
mysql> FLUSH PRIVILEGES;
```

```
mysql> quit;

$sudo service mysql restart
```

```
$mysql -u username -p
password:password
```

To refer this link [https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

#### Mysql

```
$sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf -->to change bind address -from 127.0.0.1 to 0.0.0.0
```

```
$systemctl restart mysql.service
```

```
$systemctl status mysql.service
```

### view purpose

```
SELECT User FROM mysql.user;  -->list of users
```
