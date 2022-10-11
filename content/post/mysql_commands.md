---
title: "Mysql Commands"
date: 2021-12-13T00:07:35-06:00
draft: false
category: Commands
tags:
- Development
- MySQL
- Databases
---

## Enter MySQL prompt as root user
{{< highlight bash >}}
sudo mysql -u root -p
{{< / highlight >}}

## Show Users and Databases
{{< highlight mysql >}}
show databases;
select host, user, password from mysql.user;
{{< / highlight >}}

## User Commands
{{< highlight mysql >}}
# To create a new MySQL user account, run the following command:
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'user_password';

# To grant access from another host, change the hostname part (localhost) with the remote machine IP.
# For example, to grant access from a machine with IP 10.8.0.5 you would run:
CREATE USER 'newuser'@'10.8.0.5' IDENTIFIED BY 'user_password';

# To create a user that can connect from any host, use the '%' wildcard as a host part:
CREATE USER 'newuser'@'%' IDENTIFIED BY 'user_password';

# Grant all privileges to a user account over a specific database:
GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';

# Grant all privileges to a user account on all databases:
GRANT ALL PRIVILEGES ON *.* TO 'database_user'@'localhost';

# To find the privilege(s) granted to a specific MySQL user account, use the SHOW GRANTS statement:
SHOW GRANTS FOR 'database_user'@'localhost';

# To delete a MySQL user account use the DROP USER statement:
DROP USER 'user'@'localhost'
{{< / highlight >}}


## Create Database
{{< highlight mysql >}}
# To create a new MySQL or MariaDB database issue the following command, where database_name is the name of the database you want to create:
CREATE DATABASE database_name;

# To avoid errors if the database with the same name as you are trying to create exists, use the IF NOT EXISTS statement:
CREATE DATABASE IF NOT EXISTS database_name;

# To select a database before you begin a MySQL session, use the following statement:
USE database_name;
{{< / highlight >}}
