# CLIENT-SERVER ARCHITECTURE WITH MYSQL
### Project Overview
In this project our task would be to implement a Client Server Architecture using MySQL Database Management System (DBMS).
Here two EC2 virtual servers would be located in the same local virtual network, so that they can communicate to each other using local IP addresses.
### 
### Implementation
Run the commands after opening up the terminal and connecting to EC2 instance:

`sudo apt update`
`sudo apt upgrade`

* Create and configure two Linux-based virtual servers (EC2 instances in AWS).

   Server A name - `mysql server`

   Server B name - `mysql client`
  
![Screenshot (380)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/381ddf79-4da9-469b-8418-7f41b456914a)



* Install MySQL Server software on the mysql Linux server.

`sudo apt install mysql-server`

  ![Screenshot (378)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/85a0b77b-a67a-4e77-8cb9-2a930a22d7f9)

 - Open mysql server
   
`sudo mysql`      

![Screenshot (379)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/92172f0c-eb03-4ade-bd2c-4258c12c17be)
  
* install MySQL Client software on mysql Linux server.

  

By default, both of your EC2 virtual servers are located in the same local virtual network, so they can communicate to each other using local IP addresses. Use mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so you will have to open it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, do not allow all IP addresses to reach your ‘mysql server’ – allow access only to the specific local IP address of your ‘mysql client’.

![Screenshot (381)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/cd34b7a4-e7b6-43a0-b875-c7f7c07af5f8)

* Configure MySQL server to allow connections from remote hosts.

`sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf`

Replace bind-address  = ‘127.0.0.1’ to bind-address = ‘0.0.0.0’

![Screenshot (385)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/d58a6087-b62b-4c56-b380-eaf9fee4a3b5)

- Save and close editor
- 
![Screenshot (387)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/808ff608-87f6-4670-8a59-175c317c3feb)

- Restart Mysql 
  `sudo service mysql restart`

Create user on the mysql server and grant privilleges
```
CREATE USER 'kite'@'13.42.25.14' IDENTIFIED BY 'mypass';
GRANT ALL PRIVILEGES ON *.* TO 'kite'@'13.42.25.14';
FLUSH PRIVILEGES;
```

On mysql client Linux Server connect remotely to mysql server Database Engine using mysql utility.

 `mysql -h <'mysql server-IP-address'> -P 3306 -u 'user' -p`

 ![Screenshot (391)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/977d6526-7a48-40a9-b07d-2e075493b8f7)

To check if we can connect successfully and remotely to the  MySQL server, we will  create two  databases "project5" and "project5_v2" on mysql server:

 `CREATE DATABASE project5;` 
 
`CREATE DATABASE project5_v2;`

Now we will go to mysql client server and try to access the "project5 and project5_v2"  databases created on mysql server.

`Show databases;`

![Screenshot (396)](https://github.com/ettebaDwop/dareyProject5/assets/7973831/25061a37-eb65-405b-8dad-1efb3395c578)





