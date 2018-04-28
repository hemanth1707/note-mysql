## MySQL \(Mysqladmin\) Commands for Database Administration in Linux

* We recommend you all to install or update your version by following our below article.

  [/Installation of MySQL 5.5.28 Server on RHEL/CentOS/Fedora](/Installation of MySQL 5.5.28 Server on RHEL/CentOS/Fedora)

#### 1. How to set MySQL Root password?

```
# mysqladmin -u root password YOURNEWPASSWORD
```

#### 2. How to Change MySQL Root password?

The old password is **123456 **and new password say **xyz123.**

```
mysqladmin -u root -p123456 password 'xyz123'
```

#### 3. How to check MySQL Server is running?

```
# mysqladmin -u root -p ping
Enter password:
mysqld is alive
```

#### 4. How to Check which MySQL version I am running?

```
# mysqladmin -u root -p version
Enter password:
```

#### 5. How to Find out current Status of MySQL server?

The **mysqladmin **command shows the status of **uptime **with running **threads **and **queries**.

```
# mysqladmin -u root -ptmppassword status
Enter password:
```

#### 6. How to check status of all MySQL Server Variable’s and value’s?

```
# mysqladmin -u root -p extended-status
Enter password:
```

#### 7. How to see all MySQL server Variables and Values?

```
# mysqladmin  -u root -p variables
Enter password:
```

#### 8. How to check all the running Process of MySQL server?

```
# mysqladmin -u root -p processlist
Enter password:
```

#### 9. How to create a Database in MySQL server?

```
# mysqladmin -u root -p create databasename
Enter password:
```

```
# mysql -u root -p
Enter password:

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| databasename       |
| mysql              |
| test               |
+--------------------+
8 rows in set (0.01 sec)
mysql>
```

#### 10. How to drop a Database in MySQL server?

You will be asked to confirm press ‘**y**‘.

```
# mysqladmin -u root -p drop databasename
Enter password:

Do you really want to drop the 'databasename' database [y/N] y
Database "databasename" dropped
```

#### 11. How to reload/refresh MySQL Privileges?

```
# mysqladmin -u root -p reload;
# mysqladmin -u root -p refresh
```

#### 12. How to shutdown MySQL server Safely?

```
mysqladmin -u root -p shutdown
Enter password:
```

To start/stop MySQL server.

```
# /etc/init.d/mysqld stop
# /etc/init.d/mysqld start
```

#### 13. Some useful MySQL Flush commands

```
# mysqladmin -u root -p flush-hosts--> Flush all host information from host cache.
# mysqladmin -u root -p flush-tables--> Flush all tables.
# mysqladmin -u root -p flush-threads--> Flush all threads cache.
# mysqladmin -u root -p flush-logs--> Flush all information logs.
# mysqladmin -u root -p flush-privileges--> Reload the grant tables.
# mysqladmin -u root -p flush-status--> Clear status variables.
```

#### 14. How to kill Sleeping MySQL Client Process?

```
# mysqladmin -u root -p processlist
Enter password:
+----+------+-----------+----+---------+------+-------+------------------+
| Id | User | Host      | db | Command | Time | State | Info             |
+----+------+-----------+----+---------+------+-------+------------------+
| 5  | root | localhost |    | Sleep   | 14   |       |                  |
| 8  | root | localhost |    | Query   | 0    |       | show processlist |
+----+------+-----------+----+---------+------+-------+------------------+
```

Now, run the following command with **kill **and **process ID **as shown below.

```
# mysqladmin -u root -p kill 5
Enter password:
+----+------+-----------+----+---------+------+-------+------------------+
| Id | User | Host      | db | Command | Time | State | Info             |
+----+------+-----------+----+---------+------+-------+------------------+
| 12 | root | localhost |    | Query   | 0    |       | show processlist |
+----+------+-----------+----+---------+------+-------+------------------+
# mysqladmin -u root -p kill 5,10--> to kill multiple process,then pass the process ID‘s with comma
```

#### 15. How to run multiple mysqladmin commands together?

```
# mysqladmin  -u root -p processlist status version
Enter password:
```

#### 16. How to Connect remote mysql server?

To use the **-h**\(**host**\)  with **IP Address **of remote machine.

```
# mysqladmin  -h 172.16.25.126 -u root -p
```

#### 17. How to execute command on remote MySQL server?

To see the **status **of remote **MySQL **server.

```
# mysqladmin  -h 172.16.25.126 -u root -p status
```

#### 18. How to start/stop MySQL replication on a slave server?

To refer this link [/ MySQL replication](/ MySQL replication)

```
# mysqladmin  -u root -p start-slave
# mysqladmin  -u root -p stop-slave
```

#### 19. How to store MySQL server Debug Information to logs?

```
# mysqladmin  -u root -p debug
Enter password:
```

#### 20. How to view mysqladmin options and usage?

```
# mysqladmin --help
```

For ex to refer this link [https://www.tecmint.com/mysqladmin-commands-for-database-administration-in-linux/](https://www.tecmint.com/mysqladmin-commands-for-database-administration-in-linux/)

| **Instructions** | **Commands** |
| :---: | :--- |
| Install | \# apt-get install mysql mysql-client mysql-server \(or\) yum      install mysql mysql-client mysql-server |
| Start | \# service mysqld start \(or\) service mysql start |
| Login to the root user | \# mysql -u root -p |
| Create database | mysql&gt; create database dname; |
| View database | mysql&gt; show databases; |
| Select database | mysql&gt; use dname; |
| Create table | mysql&gt;create table tname\(id integer,name varchar\(10\)\); |
| List all tables | mysql&gt;show tables; |
| View table | mysql&gt;select \* from tname; |
| Add new column | mysql&gt;alter table tname add address varchar \(20\) after        name; |
| Insert values | mysql&gt;insert into tname values\(1,'name','chennai'\); |
| Delete values | mysql&gt;delete from tname where id=1; |
| Update values | mysql&gt;update tname set address='madurai' where id=1; |
| Delete column | mysql&gt;alter table tname  drop address; |
| Rename table | mysql&gt;rename table oldname to newname; |
| Delete database | mysql&gt;drop database dname; |

For ex to refer this link [https://www.tecmint.com/gliding-through-database-mysql-in-a-nutshell-part-i/](https://www.tecmint.com/gliding-through-database-mysql-in-a-nutshell-part-i/)
