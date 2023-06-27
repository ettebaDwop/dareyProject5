# CLIENT-SERVER ARCHITECTURE WITH MYSQL
Project Overview
TASK – Implement a Client Server Architecture using MySQL Database Management System (DBMS).
### Steps
Run the commands after opening up the terminal and connecting to EC2 instance:
`sudo apt update`
`sudo apt upgrade`



* Create and configure two Linux-based virtual servers (EC2 instances in AWS).

Server A name - `mysql server`

Server B name - `mysql client`


* Install MySQL Server software on the mysql Linux server.
  
  
* install MySQL Client software on mysql Linux server.

  

By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ – allow access only to the specific local IP address of your ‘mysql client’.

* Configure MySQL server to allow connections from remote hosts.

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`

  Replace ‘127.0.0.1’ to ‘0.0.0.0’ like this:



From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH. You must use the mysql utility to perform this action.

Check that you have successfully connected to a remote MySQL server and can perform SQL queries:

Show databases;
