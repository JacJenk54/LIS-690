# Install WordPress

## Requirements
1. Check to see if system requirements are met
- `php --version`
- `mysql --version`
2. Add additional **PHP** modules for Wordpress
- `sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl`
3. Restart **Apache2** and **MySQL**
- `sudo systemctl restart apache2`
- `sudo systemctl restart mysql`

## Download and Extract
1. Change to **/var/www/html** directory
- `cd /var/www/html`
2. Download latest version of **WordPress** using `wget`
- `sudo wget https://wordpress.org/latest.tar.gz`
3. Extract package using `tar`
- `sudo tar -xzvf latest.tar.gz`

## Create Database and User
1. Switch to root Linux user
- `sudo su`
2. Login as MySQL root user
- `mysql -u root`
3. Create a new user for WordPress
- `create user 'wordpress'@'localhost' identified by 'XXXXXXXXX'`
- Replace Xs with a strong password
5. Create a new database for WordPress
- `create database wordpress;`
6. Grant all privileges to the new user
- `grant all privileges on wordpress.* to 'wordpress'@'localhost';`
7. Examine output
- `show databases;`
8. Exit MySQL prompt
- `\q`






