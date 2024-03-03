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

## Graphical Web Browser
1. IP located on GCloud under *VM insatnces*
2. View orignal webpage using *http://34.16.182.17/index.html.original*


# PHP
PHP is a server side programing language
- Interacts with databases

## Instaliation
1. Install PHP
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
2. Change the line to have **index.php** listed first eathe rthan last
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
3. Add the following code:
`<html>
<head>
<title>Broswer Detector</title>
</head>
<body>
<p>You are using the following browser to view this site:</p>

<?php
$user_agent = $_SERVER['HTTP_USER_AGENT'];

if(strpos($user_agent, 'Edge') !== FALSE) {
    $browser = 'Microsoft Edge';
} elseif(strpos($user_agent, 'Firefox') !== FALSE) {
    $browser = 'Mozilla Firefox';
} elseif(strpos($user_agent, 'Chrome') !== FALSE) {
    $browser = 'Google Chrome';
} elseif(strpos($user_agent, 'Opera Mini') !== FALSE) {
    $browser = "Opera Mini";
} elseif(strpos($user_agent, 'Opera') !== FALSE) {
    $browser = 'Opera';
} elseif(strpos($user_agent, 'Safari') !== FALSE) {
    $browser = 'Safari';
} else {
    $browser = 'Unknown';
}

if(strpos($user_agent, 'Windows') !== FALSE) {
    $os = 'Windows';
} elseif(strpos($user_agent, 'Linux') !== FALSE) {
    $os = 'Linux';
} elseif(strpos($user_agent, 'Mac') !== FALSE) {
    $os = 'Mac';
} elseif(strpos($user_agent, 'iOS') !== FALSE) {
    $os = 'iOS';
} elseif(strpos($user_agent, 'Android') !== FALSE) {
    $os = 'Android';
} else {
    $os = 'Unknown';
}

if($browser === 'Unknown' || $os === 'Unknown') {
    echo 'No browser detected.';
} else {
    echo 'Your browser is ' . $browser . ' and your operating system is ' . $os . '.';
}
?>

</body>
</html>`
4. Check the page *http://34.125.181.194*
- Should look like this:
<img width="1440" alt="Screenshot 2024-03-03 at 2 35 01 PM" src="https://github.com/JacJenk54/LIS-690/assets/157763172/e29b8dbc-b983-4f90-af97-f857b32b6424">

# MySQL

