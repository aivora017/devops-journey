# AWS LAMP Stack Deployment (Amazon Linux 2023)

##  Project Overview
This project demonstrates deploying a **LAMP Stack application** on an **AWS EC2 instance**.

LAMP is a classic 2-tier web architecture:

- **Tier 1 (Web Layer):** Apache + PHP
- **Tier 2 (Database Layer):** MariaDB

This deployment was done on AWS to understand real-world DevOps server setup.

---

## Tech Stack Used

- **Cloud Provider:** AWS
- **Service:** EC2
- **OS:** Amazon Linux 2023
- **Web Server:** Apache (httpd)
- **Database:** MariaDB
- **Backend Language:** PHP
- **Remote Access:** SSH

---

## Architecture

User Browser
|
v
Apache Web Server + PHP (EC2)
|
v
MariaDB Database (Same Instance)


Future improvement: Separate DB server for true 2-tier setup.

---

##  AWS Configuration

### Instance Details
- Instance Type: `t3.micro`
- AMI: Amazon Linux 2023
- Storage: 8GB gp2

### Security Group Rules

| Port | Service | Source |
|------|---------|--------|
| 22   | SSH     | My IP Only |
| 80   | HTTP    | Public (0.0.0.0/0) |

---

##  Step-by-Step Deployment

### 1. Connect to EC2 via SSH

ssh -i lamp-key.pem ec2-user@<EC2_PUBLIC_IP>

### 2. Update the Server

sudo dnf update -y

### 3. Install Apache Web Server

sudo yum install httpd -y
sudo systemctl enable httpd
sudo systemctl start httpd

To test

curl localhost

or 

open browser a type

http://<public Ip of instace>


### 4. Install Mariadb Data Server

sudo yum search Mariadb

this will give you a list of all the mariadb version present in the repo ready to be installed.
we have mariadb105

so we used

sudo yum install mariadb105-server -y
sudo systemctl enable mariadb
sudo systemctl start mariadb

to check if maria db is installed and running

sudo systemctl status mariadb

### 5. Configure Database

sudo mariadb
MariaDB > CREATE DATABASE ecomdb;
MariaDB > CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';
MariaDB > GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';
MariaDB > FLUSH PRIVILEGES;
MariaDB > EXIT

### 6. Load Products inventory and data into Database

cat > db-load-script.sql <<-EOF
USE ecomdb;
CREATE TABLE products (id mediumint(8) unsigned NOT NULL auto_increment,Name varchar(255) default NULL,Price varchar(255) default NULL, ImageUrl varchar(255) default NULL,PRIMARY KEY (id)) AUTO_INCREMENT=1;

INSERT INTO products (Name,Price,ImageUrl) VALUES ("Laptop","100","c-1.png"),("Drone","200","c-2.png"),("VR","300","c-3.png"),("Tablet","50","c-5.png"),("Watch","90","c-6.png"),("Phone Covers","20","c-7.png"),("Phone","80","c-8.png"),("Laptop","150","c-4.png");

EOF

sudo mysql < db-load-script.db

### 7. Change to accept php file

sudo sed -i 's/index.html/index/php/g' /etc/httpd/conf/httpd.conf

we change the httpd.conf file wo accept index.php insted of index.html

### 8. Download the code and files to the server

the files need to be place in /var/www/html/ we have our code on github repo so we directly donload the files to that loaction.

sudo git clone https://github.com/aivora017/learning-app-ecommerce.git /var/www.html/

### 9. Testing

curl http://localhost

acess the web at

http://ec2 ivp4 public ip address
