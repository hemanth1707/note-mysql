# This is the introduction page note on mysql

# MySQL

## 1.MySQL Database

| Instructions | Commands |
| :--- | :--- |
| Create | CREATE DATABASE database\_name; |
| View list of databases | SHOW DATABASES; |
| Select | USE database\_name; |
| Drop | DROP DATABASE database\_name; |

## 2.MySQL Table

| Instructions | Commands |
| :--- | :--- |
| Create | CREATE TABLE table\_name\(column\_name column\_type..\); |
| View list of  tables | SHOW TABLES; |
| Table structure | DESC table\_name; |
| View current table | SELECT \* FROM table\_name; |
| Add new column | ALTER TABLE table\_name ADD new\_column\_name column\_definition; |
| Add column with specific position | ALTER TABLE table\_name ADD new\_column\_name column\_definition AFTER column\_name; |
| Modify column definition | ALTER TABLE table\_name MODIFY column\_name definition\_name; |
| Drop column | ALTER TABLE table\_name DROP COLUMN column\_name; |
| Rename column | ALTER TABLE table\_name CHANGE COLUMN old\_name new\_name column\_definition; |
| Rename table | ALTER TABLE table\_name RENAME TO new\_table\_name; |
| Truncate--&gt;removes only data | TRUNCATE TABLE table\_name; |
| Drop--&gt;remove table | DROP TABLE table\_name; |
