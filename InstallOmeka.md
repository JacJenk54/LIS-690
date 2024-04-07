# Omeka

## Prerequisites
1. Install ImageMagick
- `sudo apt install imagemagick`
2. Enable Apache `mod_rewrite`
- `sudo a2enmod rewrite`
3. Restate Apache
- `sudo systemctl restart apache2`

## Installation
1. Use `wget` to install Omeka
- `sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`
2. Unzip Omeka
- `sudo apt install unzip`
3. Change to root user
- `sudo su`
4. Open MySQL
- `mysql -u root`
5. Create Omeka user
- `create user 'omeka'@'localhost' identified by 'OmekaPassword54!';`
6. Create Omeka database
- `create database omeka;`
7. Grant privileges to new user
- `grant all privileges on omeka.* to 'omeka'@'localhost';`
8. Examine output
- `show databases;`
- **Omeka** shown in databses
9. Exit MySQL
- `\q`
- `exit`
10. Chnage directory to **/var/www/html**
- `cd /var/www/html`
11. Rename **omeka-3.1.2** to **omeka**
- `sudo mv omeka-3.1.2 omeka`
12. Change directory to **/var/www/html/omeka**
- `cd /var/www/html/omeka`
13. Configure Omeka
- `sudo nano db.ini`
- host     = "localhost"
- username = "omeka"
- password = "OmekaPassword54!"
- dbname   = "omekadb"
13. Change file ownership
- `sudo chown -R www-data:www-data /var/www/html/omeka/files`
14. Restart Apache
- `sudo systemctl restart apache2`
15. Restart MySQL
- `sudo systemctl restart mysql`
16. Go to URL
- http://34.16.213.217/omeka/
17. Omeka PHP error
- `http://34.125.0.127/omeka/install/`

