# Apache Web Server
Apache is a web server application, and one of the most popular ones
- Web servers are software that makes websites available
- Think of the web as a file system on streroids

## Instalation
1. First update the system
- `sudo apt update`
- `sudo apt -y upgrade` = automatically updates the software
2. Search for the Apache2 package
- `apt search apache2 | head`
3. Show the Apache2 package
- `apt show apache2`
4. Install the package
- `sudo apt install apache2`
5. Check to see if Apache2 is ennabled and running
- `systemctl status apache2`
- Enabled = software will start on reboot
- Active = software is running

## Text Based Web Browser
1. Install **w3m**
- `sudo apt install w3m`
2. Visit the site
- `w3m 127.0.0.1` or
- `w3m 10.128.0.99`
3. View the IP adress
- `ip a`

## Graphical Web Browser
1. IP located on GCloud under **VM insatnces**
2. View orignal webpage using *http://34.16.182.17/index.html.original*


# PHP
PHP is a server side programing language
- Interacts with databases

## Instaliation
1. Install **PHP**
- `sudo apt install php libapache2-mod-php`
2. Restart Apache2
- `sudo systemctl restart apache2`
3. Check Apache2's status
- `systemctl status apache2`

## Check Instalation
1. Go to `/var/www/html/`
- `cd /var/www/html/`
2. Create a file called **info.php**
- `sudo nano info.php`
3. Add following text to the file
- `<?php
  phpinfo();
  ?>`
4. Visit the file using external IP adress *http://34.125.181.194/info.php*

## Configurations
1. Have Apache2 default to file **index.php** instead of **index.html**
- `cd /etc/apache2/mods-enabled/`
- `sudo cp dir.conf dir.conf.bak`
- `sudo nano dir.conf`
2. Change the line to have **index.php** listed first rather than last
- Should look like: `DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm`
3. Check configuration
- `apachectl configtest`
-  Should say **Syntax Ok**
4. Reload Apache 2
- `sudo systemctl reload apache2`
5. Restart Apache2
- `sudo systemctl restart apache2`

## Create *index.php* File
1. Go to `/var/www/html/`
- `cd /var/www/html/`
2. Create a file called **index.php**
- `sudo nano index.php`
- Add appropriate code
3. Check the page *http://34.125.181.194*
- Should look like this:
<img width="1440" alt="Screenshot 2024-03-03 at 2 35 01 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/e29b8dbc-b983-4f90-af97-f857b32b6424">

# MySQL
MySQL is a relational databade

## Installation
1. Install **MySQL**
- `sudo apt install mysql-server`
2. Check status
- `systemctl status mysql`
3. Run post installation script
- `sudo mysql_secure_installation`
4. Create a password
5. Remove anonymous users: Y
6. Disallow root login remotely: Y
7. Remove test database and access to it: Y
8. Reload privilege tables now: Y

1. Become the **root Linus user**
- `sudo su`
2. Connect to MySQL server as a root user
- `mysql -u root`
3. Show list of databases
- `show databases;`
<img width="1440" alt="Screenshot 2024-03-03 at 3 25 19 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/3bd9ef86-ca94-42b2-85d9-0931b8caf9a5">

4. Create an opac user
- `create user 'opacuser'@'localhost' identified by 'XXXXXXXXX';`
5. Create a practice database
- `create database opacdb;`
6. Grant user privilages
- `grant all privileges on opacdb.* to 'opacuser'@'localhost';`
7. Exit out of MySQL database as the root MySQL user
- `\q`
8. Exit out of Linux root user
- `exit`

## Regular User
1. Login as a Regular User
- `mysql -u opacuser -p`
2. Show databses
- `show databases;`
3. Switch to the new **opacdb** database
- `use opacdb;`
4. Create a table called **books**
`create table books (
id int unsigned not null auto_increment,
author varchar(150) not null,
title varchar(150) not null,
copyright date not null,
primary key (id)
);`
5. Confirm the table was created
- `show tables;`
- `describe books;`

## Add Records to the Table
1. Populate opacdb database with some data
2. View all the records just created
- `select * from books;`

## Basic OPAC
Link: *http://34.125.86.249/opac.php*

# Reflection
This was a long but very insightful process. Ran into some troubles along the
way but I was able to get through it. In my other classes I have only
leanred about the general concepts of OPACS, but to see how it works behind
the scenes is very insightful. It is hard to believe that prior to this class
I knew nothing about Linux or programing and now I am getting to set up
my own little OPAC.
