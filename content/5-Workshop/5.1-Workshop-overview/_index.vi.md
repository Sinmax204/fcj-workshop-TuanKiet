---
title: "Giới thiệu"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---



## Amazon VPC Endpoints

Amazon VPC Endpoints là dịch vụ cho phép các tài nguyên bên trong **Amazon Virtual Private Cloud (Amazon VPC)** kết nối trực tiếp đến các dịch vụ AWS mà không cần đi qua Internet công cộng. Toàn bộ lưu lượng được truyền trên mạng nội bộ của AWS, giúp tăng cường tính bảo mật, giảm độ trễ và đơn giản hóa kiến trúc mạng.

Hiện nay, Amazon VPC Endpoints gồm hai loại phổ biến:

- **Gateway Endpoint:** Hỗ trợ truy cập riêng tư đến **Amazon S3** và **Amazon DynamoDB** thông qua bảng định tuyến (Route Table), không cần sử dụng Internet Gateway hoặc NAT Gateway.
- **Interface Endpoint (AWS PrivateLink):** Tạo các Elastic Network Interface (ENI) trong VPC, cho phép kết nối riêng tư đến nhiều dịch vụ AWS cũng như các dịch vụ của bên thứ ba.

Việc sử dụng VPC Endpoints là một trong những khuyến nghị của AWS nhằm xây dựng hệ thống có tính bảo mật cao, đồng thời giảm chi phí và hạn chế việc truyền dữ liệu qua Internet.

---

## Tổng quan Workshop

Trong workshop này, mình sẽ tìm hiểu cách sử dụng **Amazon VPC Endpoints** để thiết lập kết nối riêng tư giữa hệ thống trong VPC và các dịch vụ AWS.

Môi trường thực hành bao gồm hai mạng VPC:

- **VPC Cloud:** Chứa các tài nguyên trên AWS như Amazon S3 Gateway Endpoint và một EC2 Instance dùng để kiểm tra kết nối.
- **VPC On-Prem:** Mô phỏng một trung tâm dữ liệu (On-Premises). Một EC2 Instance được cài đặt **strongSwan VPN** nhằm thiết lập kết nối **Site-to-Site VPN** với **AWS Transit Gateway**, cho phép hệ thống tại chỗ giao tiếp an toàn với các tài nguyên trên AWS.

Trong quá trình thực hành, mình sẽ cấu hình Gateway Endpoint và kiểm tra khả năng truy cập Amazon S3 từ môi trường On-Prem thông qua kết nối VPN. Qua đó có thể hiểu rõ cách doanh nghiệp triển khai mô hình Hybrid Cloud, đảm bảo việc truyền dữ liệu diễn ra an toàn mà không cần sử dụng Internet công cộng.

Workshop cũng giúp làm quen với một số dịch vụ và khái niệm quan trọng trên AWS như:

- Amazon VPC Endpoints
- AWS Transit Gateway
- Site-to-Site VPN
- Amazon S3
- Hybrid Cloud Networking

---

## Kiến trúc Workshop

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.1-Workshop-overview/diagram1.png" width="90%">
</p>

<p align="center">
<i>Hình 5.1. Kiến trúc tổng quan của workshop Amazon VPC Endpoints.</i>
</p>