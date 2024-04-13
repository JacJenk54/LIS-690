# KohaILS

## Create New Google Cloud VM
Create a new virtual machine
1. Click on hamburger icon (☰) in top left corner
2. Click *Computer Engine*
3. Click *VM Instances*
4. Click *Create Instance*
5. Change name to **main-ubuntu2**
6. Set Series to **E2**
7. Set Machine Type to **e2-mediun (2v CPU, 1 core, 4GB memory)**
8. Go to *Boot Disk* and hit change button
- Operating system: **Ubuntu**
- Version: Ubuntu **20.04 LTS x86/64**
- Boot disk type: **Balanced persistent disk**
- Disk size: **10GB**
- Click *Select*
9. Check *Allow HTTP Traffic* button
10. Click *Create*

## Create Google Cloud Firewall
1. Click on the hamburger icon (☰) in the top left corner
2. Click *VPC Network*
3. Click *Firewall*
4. Choose *Create a firewall rule*
- Name: **koha**
- Description: **open port 8080**
- Targets: **All instances in the network**
- Source IPv4 ranges: **add 0.0.0.0/0**
- Specified protocols and ports:
  - Click on **TCP**
  - Add **8080** in Ports box
- Click *Create*

## Server Setup
1. Update repositories
- `sudo apt uodate`
2. Upgrade servers
- `sudo apt upgrade`
3. Clear up disk space
- `sudo apt autoremove -y && sudo apt clean`
4. Intall **gnupg2**
- `sudo apt install gnupg2`
5. Rebbot
- `sudo reboot now`

## Add Koha Repository
1. Switch to **root** user
- `sudo su`
2. Add **Koha** repository to server
- `echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list
3. Add digital signature
- `wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -`

## Koha Installation
1. Update/sync new repository with Koha remote repository
- `apt update`
2. View Koha package info
- `apt show koha-common`
3. Install Koha package
- `apt install koha-common`

## Configure Koha
1. Edit configuration files for Koha
- `nano /etc/koha/koha-sites.conf`
- Change **INTRAPORT="80"** to **INTRAPORT="8080"**
2. Install and update **mysql-server**
- `apt install mysql-server`
3. Set password
- `mysqladmin -u root password MysqlPassword54!`
4. Enable URL rewriting and CGI funtionality
- `a2enmod rewrite`
- `a2enmod cgi`
5. Restart Apache 2
- `systemctl restart apache2`
6. Create database for Koha
- `koha-create --create-db bibliolib`
7. Instruct Apache 2 to listen on port 8080
- `nano /etc/apache2/ports.conf`
- Add **Listen 8080**
8. Validate Apache configuration changes
- `apachectl configtest`
9. Restart Apache 2
- `systemctl restart apache2`
10. Disable default Apache 2 setup
- `a2dissite 000-default`
11. Enable traffic compression
- `a2enmod deflate`
12. Enable **bibliolib** site
- `a2ensite bibliolib`
13. Reload Apache 2 configurations
- `systemctl reload apache2`
14. Restart Apache 2
- `systemctl restart apache2`

## Koha Web Installer
1. 



