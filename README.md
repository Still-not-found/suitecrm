# suitecrm
 #### Suitecrm installation for self-hosting
 
## Introduction

SuiteCRM is an open-source Customer Relationship Management (CRM) software solution that helps organize all the processes and activities concerning a company's sales, markets, and services administration. This article will guide you on how to install SuiteCRM on Ubuntu 20.04. 

# Installation

### Table of Contents

#### Prerequisites
* Step 1. Log in via SSH and update the system
* Step 2: Install Apache Webserver
* Step 3: Install PHP and extensions
* Step 4: Install MariaDB
* Step 5: Create a Database for SuiteCRM
* Step 6: Download SuiteCRM on Ubuntu 20.04
* Step 7: Create an Apache configuration file
* Step 8: Install SuiteCRM on Ubuntu 20.04
Step 1. Log in via SSH and update the system
Log in to your Ubuntu 20.04 VPS with SSH as a root user:

ssh root@IP_Address -p Port_number
Replace “IP_Address” and “Port_Number” with your server’s IP address and SSH port.

You can check whether you have the proper Ubuntu version installed on your server with the following command:

lsb_release -a
You should get the following output:

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 20.04.3 LTS
Release: 20.04
Codename: focal
Now, run the following command to update all installed packages to the latest available version.

apt update && sudo apt upgrade
Step 2: Install Apache Webserver
Execute the following command to install Apache webserver:

apt install apache2
To start Apache and to enable it to auto-start on server boot, run these commands:

systemctl enable apache2
systemctl start apache2
To confirm that you have properly installed Apache2, you can open your preferred web browser and type your server IP address and you should be able to view the Apache2 Ubuntu Default Page.

Step 3: Install PHP and extensions
To install PHP and the required PHP extensions, run the following command:

apt install php php-cli php-common php-curl php-mbstring php-gd php-mysql php-soap php-xml php-imap php-intl php-opcache php-json php-zip

Step 4: Install MariaDB
MariaDB is available in the Ubuntu 20.04 default OS repository. You can install it by running the following command:

apt install mariadb-server
By default, the MariaDB service will start automatically after installing it in your system. You can verify it with the following command:

systemctl status mariadb
You should get the following output:

● mariadb.service - MariaDB 10.3.32 database server
Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
Active: active (running)
Docs: man:mysqld(8)
https://mariadb.com/kb/en/library/systemd/
Main PID: 968 (mysqld)
Status: "Taking your SQL requests now..."
Tasks: 30 (limit: 2240)
Memory: 114.8M
CGroup: /system.slice/mariadb.service
└─968 /usr/sbin/mysqld
Once the installation is complete, issue the following command to secure your installation. This is optional, but strongly recommended:

mariadb_secure_installation
This script will set the MariaDB root password, disable remote root login and remove anonymous users. We suggest answering every question with the character ‘Y’ for yes.

