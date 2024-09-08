---
title: "Building a 3-Tier Application with Node.js, Express, EC2, AWS ElastiCache, and AWS RDS"
date: 2024-08-31T21:06:09+07:00
draft: false
---

## Building a 3-Tier Application with Node.js, Express, EC2, AWS ElastiCache, and AWS RDS

In this workshop, we will create a 3-tier web application using Node.js and Express. The application will be deployed on AWS EC2, with AWS ElastiCache for caching and AWS RDS for the database.

### Architecture Overview

A 3-tier architecture typically consists of the following layers:

1. **Presentation Layer**: This is the user interface of the application, usually a web page or a mobile app.
2. **Application Layer**: This contains the business logic of the application, typically implemented in a server-side language like Node.js.
3. **Data Layer**: This stores the application’s data, typically in a relational database like MySQL or PostgreSQL.

For this workshop:
- **Node.js with Express** will be used for the application layer.
- **AWS EC2** instances will host our Node.js application.
- **AWS RDS** (Relational Database Service) will host our database.
- **AWS ElastiCache** will be used to cache data for improved performance.

### Workshop Outline

1. **Set Up the AWS Environment**
   - Launch an EC2 instance
   - Set up security groups
   - Create an RDS database instance
   - Set up ElastiCache for caching

2. **Build the Node.js Application**
   - Initialize a Node.js project
   - Set up Express
   - Connect to RDS
   - Implement caching with ElastiCache

3. **Deploy the Application to AWS EC2**
   - Configure the EC2 instance for Node.js
   - Deploy the application

4. **Test the Application**
   - Verify the application functionality
   - Check caching and database connections

### Step-by-Step Instructions

#### 1. Set Up the AWS Environment

**1.1 Launch an EC2 Instance**

1. Go to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to **EC2** and click on **Launch Instance**.
3. Choose an Amazon Machine Image (AMI). Select the latest **Amazon Linux 2** AMI (64-bit x86).
4. Choose an instance type. **t2.micro** is sufficient for this workshop and is eligible for the free tier.
5. Configure instance details:
   - Network: Select the default VPC.
   - Subnet: Select a default subnet.
   - Auto-assign Public IP: Enable.
6. Add storage: Use the default of 8 GB.
7. Configure security group: Create a new security group or select an existing one.
   Ensure that your security group has the following inbound rules:
   - SSH (port 22): Allows you to connect to the instance using SSH.
   - HTTP (port 80): Allows web traffic to your application.
   - Custom TCP Rule (port 6379): For Redis if using ElastiCache with Redis engine.
   - MySQL/Aurora (port 3306): For RDS if using a MySQL database engine.
8. Launch the instance and download the key pair for SSH access.

**1.2 Set Up Security Groups**

Ensure that your security group has the following inbound rules:
- SSH (port 22): Allows you to connect to the instance using SSH.
- HTTP (port 80): Allows web traffic to your application.
- Custom TCP Rule (port 6379): For Redis if using ElastiCache with Redis engine.
- MySQL/Aurora (port 3306): For RDS if using a MySQL database engine.

**1.3 Create an RDS Database Instance**

1. Go to **RDS** in the AWS Management Console.
2. Click **Create database**.
3. Choose a database creation method: Standard Create.
4. Engine options: Select **MySQL** (or another preferred relational database engine).
5. Templates: Choose **Free tier** for this workshop.
6. Settings:
   - DB instance identifier: `workshop-db`.
   - Master username: `admin`.
   - Master password: `yourpassword`.
7. DB instance size: Select **db.t2.micro**.
8. Connectivity: Choose the default VPC and make sure to select the same subnet as your EC2 instance.
   - Enable Public Accessibility to allow EC2 to connect to RDS.
9. Additional configuration: Leave defaults or adjust as needed.
10. Click **Create database**.

**1.4 Set Up ElastiCache**

1. Navigate to **ElastiCache** in the AWS Management Console.
2. Click on **Create** and choose **Redis**.
3. Configure the cluster:
   - Name: `workshop-cache`.
   - Engine version: Select the latest stable version.
   - Node type: `cache.t2.micro` for the free tier.
4. Network: Choose the same VPC and subnet as your EC2 instance.
5. Click **Create**.

#### 2. Build the Node.js Application

**2.1 Initialize a Node.js Project**

1. SSH into your EC2 instance.
2. Install Node.js and npm:
   ```bash
   sudo yum update -y
   sudo curl -sL https://rpm.nodesource.com/setup_16.x | sudo bash -
   sudo yum install -y nodejs
