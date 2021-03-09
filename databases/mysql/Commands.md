# MySQL Cheat Sheet

**Database Management** 
 - Create a database 
	 - `mysql> CREATE DATABASE [dbname];`
 - List all databases 
	 - `mysql> SHOW DATABASES;`
 - Select a database 
	 - `mysql> use mysql;`
 - Show tables in the current database 
	 - `mysql> SHOW TABLES;`
 - Remove a database 
	 - `mysql> DROP DATABASE [dbname];` 

**User Management**
 - Create a user
	 -  `mysql> CREATE USER [user] IDENTIFIED BY 'passwd';`
 - Rename user 
	 - `mysql> RENAME USER [oldname] TO [newname];`
 - Show current user
	 -  `mysql> SELECT current_user;`
 - List users in current database 
	 - `mysql> SELECT user FROM user;` 
	 - "user" is the name of the user table for that database. This can be found with `SHOW TABLES;` 
 - List all user data in current database 
	 - `mysql> SELECT * FROM user;`
 - Show all columns in the user table 
	 - `mysql> DESC user;`
 - Delete a user 
	 - `mysql> DROP USER [user](@localhost);` 
	or `mysql> DELETE FROM mysql.user WHERE USER = [user]; mysql> FLUSH PRIVILEGES; `
 
 **User Permissions**
 - Grant a user all permissions 
	 - `mysql> GRANT ALL PRIVILEGES ON [dbname].* to [user]` 
 - Show a specific user's permissions
	-   `mysql> SHOW GRANTS FOR [user]@localhost;`

**Global Variables**
 - Set read only `mysql> SET GLOBAL read_only = ON;`

**Query Output**
 - Sometimes the output of queries looks gross. There are ways to fix this
	 -  Use pager to make the output similar to less in a regular Linux terminal so you can scroll with arrow keys when lines would normally be chopped off 
		 -  `mysql> pager less -S`
		 - `mysql> nopager` will turn off the pager

	 - Output everything vertically by appending \G in place of the semicolon at the end of queries 
		 - `mysql> SELECT * FROM user \G`


![Vertical output](https://user-images.githubusercontent.com/64932388/110540807-ef4b5800-80f4-11eb-9eb1-26701a7c035d.png | height=100)


**Linux Command Line**
 - Access MySQL 
	 - ` # mysql -u root -p`
	 - This assumes that you are trying to access the database as the root user. The -p flag will prompt you for a password
	
 - Run Queries From Command Line
	 - `# mysql -u [uname] -p [dbname] -e "query"`
		 - **Be very careful with this!** If you pass sensitive data into the command line with this, such as changing a user's password, it will be stored in your bash history.
	 - You can optionally save the query output to a file:
		 - `# mysql -u [uname] -p [dbname] -e "query" > [filename]`
 - Manage Service
		 - `# systemctl status/start/stop mysql`
