# 🚀 AWS LAMP Stack Deployment (Amazon Linux 2023)

## ✅ Project Overview

This project demonstrates deploying a **2-tier LAMP Stack web application** on an **AWS EC2 instance**.

LAMP is a classic production architecture:

- **Tier 1 (Web Layer):** Apache + PHP  
- **Tier 2 (Database Layer):** MariaDB  

The goal of this project was to gain real-world DevOps experience in:

- Launching and securing EC2 instances  
- Installing and configuring web + database services  
- Deploying an application backed by a database  
- Documenting deployment steps for reproducibility  


## ✅ Tech Stack Used

| Component | Technology |
|----------|------------|
| Cloud Provider | AWS |
| Service | EC2 |
| Operating System | Amazon Linux 2023 |
| Web Server | Apache (httpd) |
| Database Server | MariaDB 10.5 |
| Backend | PHP |
| Access Method | SSH |

## ✅ Architecture

```text
User Browser
     |
     v
Apache + PHP Web Server (Tier 1)
     |
     v
MariaDB Database Server (Tier 2)

✅ AWS Configuration
Instance Details
Instance Type: t3.micro

AMI: Amazon Linux 2023

Storage: 8GB gp2

Security Group Rules
Port	Service	Access
22	SSH	My IP Only
80	HTTP	Public (0.0.0.0/0)

✅ Database port is NOT exposed publicly for security best practices.

✅ Step-by-Step Deployment
1. Connect to EC2 via SSH

ssh -i lamp-key.pem ec2-user@<EC2_PUBLIC_IP>
2. Update the Server

sudo dnf update -y
3. Install Apache Web Server

sudo dnf install httpd -y
sudo systemctl enable httpd
sudo systemctl start httpd
Verify Apache

curl localhost
Open in browser:

http://<EC2_PUBLIC_IP>
4. Install MariaDB Database Server
Amazon Linux provides versioned packages:

sudo dnf install mariadb105-server -y
sudo systemctl enable mariadb
sudo systemctl start mariadb
Verify MariaDB Status
sudo systemctl status mariadb
Secure Installation
sudo mysql_secure_installation

5. Configure Database
Login:

sudo mariadb
Run:

CREATE DATABASE ecomdb;

CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';

GRANT ALL PRIVILEGES ON ecomdb.* TO 'ecomuser'@'localhost';

FLUSH PRIVILEGES;

EXIT;
6. Load Product Inventory into Database
Create the SQL file:

nano db-load-script.sql
Paste:
USE ecomdb;

CREATE TABLE products (
  id MEDIUMINT(8) UNSIGNED NOT NULL AUTO_INCREMENT,
  Name VARCHAR(255) DEFAULT NULL,
  Price VARCHAR(255) DEFAULT NULL,
  ImageUrl VARCHAR(255) DEFAULT NULL,
  PRIMARY KEY (id)
);

INSERT INTO products (Name, Price, ImageUrl) VALUES
("Laptop","100","c-1.png"),
("Drone","200","c-2.png"),
("VR","300","c-3.png"),
("Tablet","50","c-5.png"),
("Watch","90","c-6.png"),
("Phone Covers","20","c-7.png"),
("Phone","80","c-8.png"),
("Laptop","150","c-4.png");
Load it:

sudo mysql < db-load-script.sql
7. Configure Apache to Support PHP Index
Edit Apache config:

sudo sed -i 's/index.html/index.php/g' /etc/httpd/conf/httpd.conf
Restart Apache:

sudo systemctl restart httpd
8. Deploy Application Code
Clone the application repository:

sudo git clone https://github.com/aivora017/learning-app-ecommerce.git /var/www/html/
Set permissions:
sudo chown -R apache:apache /var/www/html/

9. Final Testing
Test locally:
curl localhost
Access in Browser:
http://<EC2_PUBLIC_IP>

✅ The e-commerce application should load successfully with products from MariaDB.

✅ Outcome
Successfully deployed a working LAMP stack application on AWS EC2

Configured Apache + PHP web layer and MariaDB backend

Populated database with inventory data

Verified live deployment through browser testing

✅ Key Learnings
Launching and securing AWS EC2 infrastructure

Managing services using systemctl

Installing packages with dnf on Amazon Linux

Understanding Tier 1 vs Tier 2 deployment design

Importance of restricting database exposure in security groups





