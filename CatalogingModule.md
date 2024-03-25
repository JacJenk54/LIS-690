# Bare Bones Cataloging Module

## HTML Page and PHP Cataloging Page
1. `cd /var/www/html`
2. `sudo mkdir cataloging`
3. `cd cataloging`
4. `sudo nano index.html`
5. Insert following code into **index.html**
`
<!DOCTYPE html>
<html>
<head>
    <title>Enter Records</title>
</head>
<body>
    <h1>OPAC Library Administration</h1>

    <p>This is the library administration page for entering records into the OPAC.</p>
    <p>Please do not use this page unless you are an authorized cataloger.</p>

    <form action="insert.php" method="post">
        <label for="author">Author:</label>
        <input type="text" name="author" id="author" required><br><br>

        <label for="title">Book Title:</label>
        <input type="text" name="title" id="title" required><br><br>

        <label for="publisher">Publisher:</label>
        <input type="text" name="publisher" id="publisher" required><br><br>

        <label for="copyright">Copyright:</label>
        <input type="date" id="copyright" name="copyright">

        <input type="submit" value="Submit">
    </form>
</body>
</html>
`
6. Go to *http://34.125.56.111/cataloging/*

## PHP Insert Script
1. `sudo nano insert.php`
2. Insert the following code into **insert.php**
- Repleace instances of **11.111.111.111** with **34.125.56.111**
`
<?php

// Load MySQL credentials
require_once '../login.php';

// Establish connection
$conn = mysqli_connect($db_hostname, $db_username, $db_password) or
  die("Unable to connect");

// Open database
mysqli_select_db($conn, $db_database) or
  die("Could not open database '$db_database'");

// Prepare and bind SQL statement
$stmt = $conn->prepare("INSERT INTO books (author, title, publisher, copyright) VALUES (?, ?, ?, ?)");
$stmt->bind_param("ssss", $author, $title, $publisher, $copyright);

// Set parameters and execute statement
$author = $_POST["author"];
$title = $_POST["title"];
$publisher = $_POST["publisher"];
$copyright = $_POST["copyright"];

if ($stmt->execute() === TRUE) {
    echo "New record created successfully";
} else {
    echo "Error: " . $stmt->error;
}

// Close statement and connection
$stmt->close();
$conn->close();

echo "<p>Return to the cataloging page: <a href='http://11.111.111.111/cataloging/'>http://11.111.111.111/cataloging/</a></p>";
?>
`
3. Reload *http://34.125.56.111/cataloging/*

## Add Security
1. Creat a password
- `sudo htpasswd -c /etc/apache2/.htpasswd libcat`
- Enter password
2. `cd /etc/apache2/`
3. Make a backup
- `sudo cp apache2.conf bak.apache2.conf`
4. `sudo nano apache2.conf`
- Go to line 172 (use **^_** to get there)
- Change `AllowOverride None` to `AllowOverride All`
5. `cd /var/www/html/cataloging`
6. `sudo nano .htaccess`
7. Insert the following code into **.htaccess**
`
AuthType Basic
AuthName "Authorization Required"
AuthUserFile /etc/apache2/.htpasswd
Require valid-user
`
8. Check the configuartion file
`apachectl configtest`
9. If it reads **Syntax OK` restart Apache 2
`sudo systemctl restart apache2`
10. Reload *http://34.125.56.111/cataloging/*
- Should be greeted with a login page
- Sign in using **libcat**

## Ownership
1. Change group ownership of **/var/www/html to www-data**
` sudo chown :www-data /var/www/html`
2. Set **setgid bit** on **/var/www/html**
` sudo chmod -R g+s /var/www/html`
