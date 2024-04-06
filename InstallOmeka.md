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
7. Grant priva

