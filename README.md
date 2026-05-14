Laravel Deployment on AWS EC2 (Ubuntu + LAMP Stack)
Overview
This project demonstrates deploying a Laravel 13 PHP application on an AWS EC2 Ubuntu instance using a Bash automation script to configure a full LAMP stack (Apache, MySQL, PHP 8.3).
________________________________________
Phase 1: EC2 Provisioning
Launched an Ubuntu 22.04 LTS t3.micro EC2 instance named Laravel-Server with a configured key pair and security group allowing SSH (22), HTTP (80), and HTTPS (443).
EC2 Instance Successfully Launched  

Instance Summary — Running State & Public IP (98.89.38.240)  

Instances List — Running with 3/3 Status Checks Passed 
 
________________________________________
Phase 2: SSH Access
Connected securely to the EC2 instance via SSH using the .pem key pair. Updated system packages and confirmed the Ubuntu environment.
SSH Login — Ubuntu Server Connected  

Confirmed Ubuntu OS — uname -a and whoami Output 


 
________________________________________
Phase 3: Bash Automation Script (LAMP Stack)
Created and executed deploy-LAMP-stack.sh to automate the full server setup. The script installs Apache, MySQL, PHP, Composer, and Git.
Note: PHP 8.2 was initially unavailable from the default Ubuntu repos. The ondrej/php PPA was added to resolve this, then PHP was upgraded to 8.3 to satisfy Laravel 13's requirements.
Script Execution — PHP PPA Error Encountered and Resolved  

Script Complete — PHP 8.2, Composer 2.9.8, Git 2.43.0 Verified  






Script file: deploy-LAMP-stack.sh
________________________________________
Phase 6: MySQL Configuration
Secured MySQL, created a dedicated database and user for the Laravel application, and granted the necessary privileges.
MySQL — laravel_db Database Created and Verified  




________________________________________
Phase 4 & 5: Laravel Deployment & Apache Configuration
Cloned the Laravel 13 repository from GitHub, installed Composer dependencies, configured .env with database credentials, generated the app key, ran migrations, and configured the Apache Virtual Host to serve the Laravel /public directory.
Apache Virtual Host Configured — Syntax OK + Active (Running)  
|

________________________________________
Phase 7: Live Application
The Laravel application is publicly accessible at: http://98.89.38.240
Laravel 13 App Running in Browser 


________________________________________
Tech Stack
•	AWS EC2 — Ubuntu 22.04 LTS (t3.micro)
•	Apache 2.4
•	MySQL 8.0
•	PHP 8.3
•	Laravel 13.9.0
•	Composer 2.9.8
•	Git 2.43.0

