---
title: "Xây dựng ứng dụng 3 tầng với Node.js, Express, EC2, AWS ElastiCache và AWS RDS"
date: 2024-08-31T21:06:09+07:00
draft: false
---

## Xây dựng ứng dụng 3 tầng với Node.js, Express, EC2, AWS ElastiCache và AWS RDS

Trong workshop này, chúng ta sẽ xây dựng một ứng dụng web 3 tầng sử dụng Node.js và Express. Ứng dụng sẽ được triển khai trên EC2 của AWS, với ElastiCache để cải thiện hiệu suất thông qua bộ nhớ đệm, và RDS (Relational Database Service) để quản lý cơ sở dữ liệu.

**Kiến trúc 3 tầng** là một mô hình kiến trúc phổ biến, được chia thành ba lớp chính:

1. **Lớp trình bày (Presentation Layer)**: Đây là giao diện người dùng của ứng dụng, có thể là một trang web hoặc ứng dụng di động.
2. **Lớp ứng dụng (Application Layer)**: Nơi chứa logic nghiệp vụ của ứng dụng, thường được triển khai bằng các ngôn ngữ phía server như Node.js.
3. **Lớp dữ liệu (Data Layer)**: Lưu trữ dữ liệu của ứng dụng, thường là cơ sở dữ liệu quan hệ như MySQL hoặc PostgreSQL.

Trong workshop này, chúng ta sẽ sử dụng:

- **Node.js và Express** cho lớp ứng dụng.
- **AWS EC2** để host ứng dụng Node.js.
- **AWS RDS** để quản lý cơ sở dữ liệu quan hệ.
- **AWS ElastiCache** để lưu trữ cache, cải thiện hiệu suất truy cập dữ liệu.

Qua workshop này, bạn sẽ học cách triển khai một ứng dụng web hoàn chỉnh và tối ưu hóa hiệu suất của nó bằng các dịch vụ AWS.
