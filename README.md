# MySQL on VM vs Managed Service 

## Overview

This repo compares two deployment options for MySQL on Google Cloud Platform (GCP):

1. **Self-managed MySQL on a Compute Engine VM**
2. **Managed MySQL using Cloud SQL**

Both environments were tested using Python, SQLAlchemy, and pandas to create a database, write a table, and read the row count.

## Cloud Region
- Cloud provider: Google Cloud Platform
- Regison: us-central1
- VM zone: us-central1-c
- Managed MySQL edition: MySQL 8.0

## High-Level Steps to Reproduce


### VM Path (Self-Managed MySQL)
1. Create a Firewall Rule for port 22 and 3306
2. Create a GCP Compute Engine VM (Ubuntu)
3. Update Install MySQL Server on the VM SSH
4. Create MySQL user with external access
5. Use NANO to edit "/etc/mysql/mysql.conf.d/mysqld.cnf → set bind-address = 0.0.0.0" and restart MySQL service
6. Update .env with VM credientials 
7. Run vm_demo.py to create database and table using SQLAlchemy


### Managed Path (Cloud SQL MySQL)
1. Create MySQL instance in Cloud SQL with MySQL 8.0, 1 vCPU, 3.75 GB RAM
2. Enable Public IP and add your home IP to the Authorized Networks list
3. Create database assignmentdb
4. Connect to Cloud Shell as root
5. Drop and recreate app user "xiao" with Privileges
6. Update .env with CLoud SQL credentials
7. Run managed_demo.py

## Connection Strings with No Secrets
### VM MySQL
```
mysql+pymysql://xiao:*****@136.112.146.81:3306
```
### Managed Cloud MySQL
```
mysql+pymysql://xiao:*****@104.197.139.224:3306
```


## Screenshots Summary 

### VM Screenshots

![firewall](screenshots/vm/firwall.png)
![instanceOV](screenshots/vm/instanceoverview.png)
![instanceOV2](screenshots/vm/instanceOVpt2.png)
![screenshots/vm/user.png](screenshots/vm/user.png)
![screenshots/vm/NANO.png](screenshots/vm/NANO.png)
![screenshots/vm/vsvm.png](screenshots/vm/vsvm.png)
![screenshots/vm/final.png](screenshots/vm/final.png)



### Managed Cloud MySQL Screenshots

![screenshots/managed/1.png](screenshots/managed/1.png)
![screenshots/managed/addIP.png](screenshots/managed/addIP.png)
![screenshots/managed/connection.png](screenshots/managed/connection.png)
![screenshots/managed/assignmentdb.png](screenshots/managed/assignmentdb.png)
![screenshots/managed/ssh1.png](screenshots/managed/ssh1.png)
![screenshots/managed/userredo.png](screenshots/managed/userredo.png)
![screenshots/managed/vscodecomplete.png](screenshots/managed/vscodecomplete.png)
![screenshots/managed/finalssh.png](screenshots/managed/finalssh.png)