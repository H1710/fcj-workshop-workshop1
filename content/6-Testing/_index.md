---
title: "Testing Result"
date: 2024-09-22
weight: 6
chapter: false
pre: "<b> 6. </b>"
---

## 6. Testing Result

1. Send request to EC2 server to create user, when create user, cache is invalidate
   ![alt text](CreateUser.png)
2. Check RDS Mysql
   ![alt text](CheckMySQL.png)
3. Send request to EC2 server to get user, if redis is invalidate, write new data to redis
   ![alt text](GetUsers.png)
4. Check Redis
   ![alt text](CheckRedis.png)
