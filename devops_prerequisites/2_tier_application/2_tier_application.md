## kodekloud - ecommerce application

kodefloud -ecommerce is a 2 tier application 
it is a LAMP stack application
L - Linux
A - apache
M - mariadb
P - php

we deployed this application in a lab environment of kodekloud

single node application
- we first delpoyed the application on a single machine or can be said everything on a single server which can also be called as single node application.
- in single node we made changes to apache config file at /etc/httpd/conf/httpd.conf 
- the changes we made were to used index.php insted of html as we used php fles here

multi node application
- then we even deployed it in a multi server environment
- in multi server environment we installed database in first server and web services like like appache and php on the other server.
- here we made changes to the apache config file at etc/httpd/conf/httpd.conf
- we made the changes to use php file 

# LAMP Two-Tier Application Deployment

## ✅ Overview
This project demonstrates deployment of a **two-tier LAMP stack application**.

- Tier 1: Apache Web Server + PHP
- Tier 2: MariaDB Database Server

This is a common real-world architecture used in production systems.

---

## ✅ Tech Stack

- Linux (Ubuntu)
- Apache2 (Web Server)
- MariaDB (Database)
- PHP (Backend)

---

## ✅ Architecture

User Request → Apache + PHP (Tier 1) → MariaDB (Tier 2)

---

## ✅ Deployment Steps

Here is how to deploy it in centos

## Deploy Pre-Requisites

1. Install FirewallD

```
sudo yum install -y firewalld
sudo systemctl start firewalld
sudo systemctl enable firewalld
sudo systemctl status firewalld
```

## Deploy and Configure Database

1. Install MariaDB

```
sudo yum install -y mariadb-server
sudo vi /etc/my.cnf
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

2. Configure firewall for Database

```
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload
```

3. Configure Database

```
$ mysql
MariaDB > CREATE DATABASE ecomdb;
MariaDB > CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';
MariaDB > GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';
MariaDB > FLUSH PRIVILEGES;
```

4. Load Product Inventory Information to database

Create the db-load-script.sql

```
cat > db-load-script.sql <<-EOF
USE ecomdb;
CREATE TABLE products (id mediumint(8) unsigned NOT NULL auto_increment,Name varchar(255) default NULL,Price varchar(255) default NULL, ImageUrl varchar(255) default NULL,PRIMARY KEY (id)) AUTO_INCREMENT=1;

INSERT INTO products (Name,Price,ImageUrl) VALUES ("Laptop","100","c-1.png"),("Drone","200","c-2.png"),("VR","300","c-3.png"),("Tablet","50","c-5.png"),("Watch","90","c-6.png"),("Phone Covers","20","c-7.png"),("Phone","80","c-8.png"),("Laptop","150","c-4.png");

EOF
```

Run sql script

```

sudo mysql < db-load-script.sql
```


## Deploy and Configure Web

1. Install required packages

```
sudo yum install -y httpd php php-mysqlnd
sudo firewall-cmd --permanent --zone=public --add-port=80/tcp
sudo firewall-cmd --reload
```

2. Configure httpd

Change `DirectoryIndex index.html` to `DirectoryIndex index.php` to make the php page the default page

```
sudo sed -i 's/index.html/index.php/g' /etc/httpd/conf/httpd.conf
```

3. Start httpd

```
sudo systemctl start httpd
sudo systemctl enable httpd
```

4. Download code

```
sudo yum install -y git
sudo git clone https://github.com/kodekloudhub/learning-app-ecommerce.git /var/www/html/
```

5. Update index.php

Update [index.php](https://github.com/kodekloudhub/learning-app-ecommerce/blob/13b6e9ddc867eff30368c7e4f013164a85e2dccb/index.php#L107) file to connect to the right database server. In this case `localhost` since the database is on the same server.

```
sudo sed -i 's/172.20.1.101/localhost/g' /var/www/html/index.php

              <?php
                        $link = mysqli_connect('172.20.1.101', 'ecomuser', 'ecompassword', 'ecomdb');
                        if ($link) {
                        $res = mysqli_query($link, "select * from products;");
                        while ($row = mysqli_fetch_assoc($res)) { ?>
```

> ON a multi-node setup remember to provide the IP address of the database server here.
```
sudo sed -i 's/172.20.1.101/localhost/g' /var/www/html/index.php
```

5. Create and Configure the `.env` File

   Create an `.env` file in the root of your project folder.

   ```sh
   cat > /var/www/html/.env <<-EOF
   DB_HOST=localhost
   DB_USER=ecomuser
   DB_PASSWORD=ecompassword
   DB_NAME=ecomdb
   EOF

6. Update `index.php`

   Update the `index.php` file to load the environment variables from the `.env` file and use them to connect to the database.

   ```php
   <?php
   // Function to load environment variables from a .env file
   function loadEnv($path)
   {
       if (!file_exists($path)) {
           return false;
       }

       $lines = file($path, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);
       foreach ($lines as $line) {
           if (strpos(trim($line), '#') === 0) {
               continue;
           }

           list($name, $value) = explode('=', $line, 2);
           $name = trim($name);
           $value = trim($value);
           putenv(sprintf('%s=%s', $name, $value));
       }
       return true;
   }

   // Load environment variables from .env file
   loadEnv(__DIR__ . '/.env');

   // Retrieve the database connection details from environment variables
   $dbHost = getenv('DB_HOST');
   $dbUser = getenv('DB_USER');
   $dbPassword = getenv('DB_PASSWORD');
   $dbName = getenv('DB_NAME');

   ?>

   ON a multi-node setup, remember to provide the IP address of the database server in the .env file.


7. Test

```
curl http://localhost
```


## Lessons Learned

- LAMP is a common production stack.
- Apache serves PHP applications.
- MariaDB handles backend storage.
- PHP connects to MariaDB using `php-mysql`.
- Service management is done via `systemctl`.
