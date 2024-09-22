---
title: "Launch an RDS Instance"
date: 2024-09-22
weight: 3
chapter: false
pre: "<b> 3. </b>"
---

## 3. Launch a RDS Instance

1. Go to the [AWS Launch RDS Instance Console].
   ![alt text](RDSConsole.png)
2. Set RDS Networking
   ![alt text](RDSNetworking.png)
3. Launch the instance.
4. Download the RPM file

```bash
sudo wget https://dev.mysql.com/get/mysql80-community-release-el9-1.noarch.rpm
```

5. Install RPM file

```bash
sudo dnf install mysql80-community-release-el9-1.noarch.rpm -y
```

6. You need the public key of mysql to install the software.

```bash
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
```

7. If you need server:
   sudo dnf install mysql-community-server -y
8. SSH to EC2
9. Access RDS instance in EC2

```bash
mysql -h <Your Database Host> -P <Port> -u <Username> -p
```

10. Create workshop database

```bash
create database workshop;
```

11. Create user table

```bash
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255)
);
```
