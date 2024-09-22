---
title: "Kết quả kiểm tra"
date: 2024-09-22
weight: 6
chapter: false
pre: "<b> 6. </b>"
---

## 6. Kết quả kiểm tra

1. Gửi yêu cầu tới máy chủ EC2 để tạo người dùng. Khi tạo người dùng, bộ nhớ cache sẽ được làm mới.  
   ![alt text](CreateUser.png)

2. Kiểm tra MySQL RDS.  
   ![alt text](CheckMySQL.png)

3. Gửi yêu cầu tới máy chủ EC2 để lấy người dùng. Nếu Redis không còn dữ liệu, hệ thống sẽ ghi dữ liệu mới vào Redis.  
   ![alt text](GetUsers.png)

4. Kiểm tra Redis.  
   ![alt text](CheckRedis.png)
