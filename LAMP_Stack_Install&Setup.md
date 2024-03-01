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
5. Check to see if Apacher2 is ennabled and running
- `systemctl status apache2`
- Enabled = software will start on reboot
- Active = software is running

## Text Based Web Browser
1. Install `w3m`
- `sudo apt install w3m`
2. Visit the site
- `w3m 127.0.0.1` or
- `w3m 10.128.0.99`
3. View the IP adress
- `ip a`

## Graphical Browser
1. IP located on GCloud under *VM insatnces*
2. View orignal webpage using *http://34.16.182.17/index.html.original*


# PHP


# MySQL

