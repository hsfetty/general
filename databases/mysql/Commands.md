# MySQL Cheat Sheet

**Database Management** 
 - Create a database `CREATE DATABASE [ex_db];`
 - List all databases `SHOW DATABASES;`
 - Select a database `use mysql;`
 - Show tables in the current database `SHOW TABLES;`
 - Remove a database `DROP DATABASE [ex_db];`

**User Management**
 - Create a user `CREATE USER hsfetty IDENTIFIED BY 'pass123';`
 - Show current user `SELECT current_user;`
 - Show user permissions `SHOW GRANTS FOR hsfetty@localhost;`
 - List users in current database `SELECT user FROM user;`
		 - Where "user" is the name of the user table for that database. This can be found with `SHOW TABLES;` 
 - List all user data in current database `SELECT * FROM user;`
 - Show all columns in the user table `DESC user;`
 - Delete a user `DROP USER hsfetty@localhost;`
 
 **User Permissions**
 - Grant a user all permissions `GRANT ALL PRIVILEGES ON ex_database.* to hsfetty`

**Global Variables**
 - Set read only `SET GLOBAL read_only = ON;`

**Query Output**

 - Sometimes the output of queries looks gross. There are ways to fix this
		 - Output similar to less in a regular terminal so you can scroll with arrow keys when lines would normally be chopped off `pager less -S`
		 - To turn off the pager, run `nopager`
		 - Output everything vertically by appending \G in place of the semicolon at the end of queries `SELECT * FROM user \G`

**Linux Command Line**

 - Access MySQL `mysql -u root -p`
		 - This assumes that you are trying to access the database as the root user. The -p flag will prompt you for a password
	
 - Run Queries From Command Line
		 - `mysql -u [uname] -p [dbname] -e "query"`
		 - **Be very careful with this!** If you pass sensitive data into the command line with this, such as changing a user's password, it will be stored in your bash history.
		 - You can optionally save the query output to a file:
		 - `mysql -u [uname] -p [dbname] -e "query" > [filename]`
 - Manage Service
		 - `systemctl status/start/stop mysql`

