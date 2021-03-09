# MySQL Hardening

Before you dive in, it is important to first stop and ask yourself what the purpose for MySQL is. Keep this in mind as you are determining what users, tables, and databases are necessary.

**Database Security** 
 - Get rid of extraneous databases and tables
>  `mysql> SHOW DATABASES;` List all databases
>   `mysql> DROP DATABASE [dbname];` Remove a database if it is unnecessary
>   `mysql> use [dbname];` Select a database to look at
>   `mysql> SHOW TABLES;` List all tables in the current database.
>   `mysql> SELECT * FROM [tname];` Look at what is stored in a table
>   `mysql> DROP TABLE [tname];` If you determine the table is extraneous

**User Security**
 - By default, there is no root password. Even if there is one, change it.
	 - `mysql> ALTER USER 'root'@localhost IDENTIFIED BY '[newpass]';`
 - Rename root user
	 - `mysql> RENAME USER root TO [newname];`
 - Remove anonymous user, if exists
	 - `mysql> DROP USER "";`
	 - or `mysql> mysql> DELETE FROM mysql.user WHERE USER = "";`
 - Get rid of extraneous users
> `mysql> SHOW DATABASES;` List all databases
> `mysql> use [dbname];` Choose a database to work with
> `mysql> SHOW TABLES;` View tables in that database. Locate which would hold user info
> `mysql> SELECT * FROM [user_table];` To view user
> `mysql> DROP USER [uname];` To delete a user
> `mysql> FLUSH PRIVILEGES;` Reload grant tables and put changes into effect
 

**Practice Least Privilege**

 - Read only: You can enable a read-only system, which says that only users with "super"
   privileges can perform updates. This is disabled by default.
	 - `mysql> SET GLOBAL read_only = ON/OFF;`
 - Super Read Only: This prohibits even users with super privileges from making changes
	 - `mysql> SET GLOBAL super_read_only = ON/OFF;`

**Remove History**
Putting passwords and other sensitive information into the MySQL command line can be very dangerous. When you are done, delete your MySQL history

 - `# cat /dev/null > ~/mysql_history`

**References**
[MySQL Privilege](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html)
