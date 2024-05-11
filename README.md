# Deploying WordPRess Website in AWS

The architecture for deploying a WordPress website on AWS revolves around several key services. At its core, an EC2 instance serves as the virtual server running the WordPress application. RDS manages the relational database, ensuring efficient data storage and management. Route 53 handles domain registration and DNS routing, directing traffic to the EC2 instance. Additionally, S3 provides scalable object storage for static files, while CloudFront caches and delivers content globally, enhancing performance. ACM supplies SSL/TLS certificates for secure connections, and CloudWatch monitors resource health and performance. Security groups and IAM roles enforce security measures, controlling access and traffic flow. This integrated architecture ensures a scalable, reliable, and secure environment for hosting WordPress websites on AWS.

![Screenshot (284)](https://github.com/neelima458/wordpress-aws-deployement/assets/72330546/c04eb4a7-724f-495f-962c-01f0cfd508d9)

## Prerequisites
 1. An AWS account
 2. Basic knowledge of AWS services
 3. Basic knowledge of WordPress
## Step 1: Launch an EC2 Instance 
 1. Log in to the AWS Management Console.
 2. Navigate to the EC2 dashboard.
 3. Launch a new EC2 instance using an Ubuntu AMI (Amazon Machine Image).
 4. Configure security groups to allow inbound traffic on ports 80 (HTTP) and 443 (HTTPS).
## Step 2: Set Up a Database with RDS
 1. Navigate to the RDS dashboard.
 2. Launch a new RDS instance with MySQL or MariaDB as the database engine.
 3. Note down the database endpoint, username, and password for WordPress configuration.
## Step 3: Connect to Your EC2 Instance
 1. SSH into your EC2 instance using the provided key pair.
```
sh
--------------------------------------------------------
ssh -i your-key.pem ubuntu@ec2-instance-ip
```
## Step 4: Install LAMP Stack and WordPress
 1. Update the package index and install Apache, MySQL, PHP, and other necessary packages.
```
lua
--------------------------------------------------------
sudo apt update
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
```
 2. Download and extract the latest version of WordPress.
 ```
arduino
---------------------------------------------------------
wget https://wordpress.org/latest.tar.gz
tar -xzvf latest.tar.gz
```
 3. Move WordPress files to the Apache web root directory.
```
bash
sudo mv wordpress/* /var/www/html/
```
 4. Configure WordPress to use the RDS database.
```
arduino
--------------------------------------------------------
cd /var/www/html
sudo mv wp-config-sample.php wp-config.php
sudo nano wp-config.php
```
   Update the database connection details in the wp-config.php file.
 5. Set the correct permissions for WordPress files.
```
bash
--------------------------------------------------------
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```
## Step 5: Access Your WordPress Website
 1. Open a web browser and navigate to your EC2 instance's public IP address.
 2. Follow the WordPress installation wizard to set up your website.
 3. Complete the installation by providing necessary information such as site title, username, password, etc.




    
