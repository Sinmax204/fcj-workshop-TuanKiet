---
title: "Blog 2"
date: 2026-05-17
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---



# AWS Architecture Blog | Điều mình học được về Amazon VPC – Nền tảng của mọi kiến trúc trên AWS

Trong quá trình tìm hiểu AWS, mình thường dành nhiều thời gian cho các dịch vụ như Amazon EC2, Amazon S3 hay AWS Lambda. Tuy nhiên, càng học và thực hành nhiều, mình càng nhận ra rằng trước khi triển khai bất kỳ ứng dụng nào trên Cloud, điều quan trọng nhất không phải là lựa chọn máy chủ hay dịch vụ lưu trữ, mà là xây dựng một kiến trúc mạng hợp lý.

Đó cũng là lý do mình bắt đầu tìm hiểu về **Amazon Virtual Private Cloud (Amazon VPC)** – một trong những dịch vụ nền tảng và quan trọng nhất của AWS.

---

## Kiến trúc tổng quan

<p align="center">
    <img src="/Sinmax204/fcj-workshop-TuanKiet/images/3-BlogsPosted/blog2.jpg" width="100%">
</p>

<p align="center">
<i>Hình 3.2. Kiến trúc cơ bản của Amazon VPC với Public Subnet, Private Subnet, Application Load Balancer, Amazon EC2 và Amazon RDS.</i>
</p>

---

## 1. Amazon VPC là gì?

Amazon VPC (Virtual Private Cloud) cho phép người dùng tạo một mạng riêng ảo trên nền tảng AWS để triển khai và quản lý các tài nguyên như Amazon EC2, Amazon RDS hay Application Load Balancer.

Có thể hình dung VPC giống như một trung tâm dữ liệu riêng trên Cloud, nơi người dùng có toàn quyền kiểm soát việc cấu hình địa chỉ IP, định tuyến mạng và chính sách bảo mật.

Trong một VPC, chúng ta có thể:

- Thiết lập dải địa chỉ IP (CIDR Block).
- Tạo Public Subnet và Private Subnet.
- Cấu hình Route Table để định tuyến lưu lượng.
- Kết nối Internet thông qua Internet Gateway hoặc NAT Gateway.
- Thiết lập Security Group và Network ACL để kiểm soát truy cập.

Theo mình, đây là bước đầu tiên và cũng là nền tảng quan trọng nhất khi xây dựng hạ tầng trên AWS.

---

## 2. Vì sao cần tách Public Subnet và Private Subnet?

Một kiến trúc AWS hiện đại thường chia hệ thống thành hai vùng mạng riêng biệt.

**Public Subnet** chứa các tài nguyên cần truy cập Internet như:

- Application Load Balancer
- Bastion Host
- NAT Gateway

Trong khi đó, **Private Subnet** được sử dụng để triển khai:

- Amazon EC2 chạy ứng dụng.
- Amazon RDS.
- Các dịch vụ nội bộ không cần truy cập trực tiếp từ Internet.

Việc phân tách này giúp giảm đáng kể bề mặt tấn công, đồng thời nâng cao tính bảo mật của toàn bộ hệ thống.

---

## 3. Security Group và Network ACL khác nhau như thế nào?

Ban đầu mình khá dễ nhầm lẫn giữa Security Group và Network ACL.

Sau khi tìm hiểu tài liệu AWS, mình nhận thấy:

### Security Group

- Hoạt động ở mức tài nguyên (Instance Level).
- Chỉ cho phép các kết nối được khai báo.
- Có tính **Stateful**, nghĩa là lưu lượng phản hồi sẽ được tự động cho phép.

### Network ACL

- Hoạt động ở mức Subnet.
- Hỗ trợ cả quy tắc Allow và Deny.
- Có tính **Stateless**, vì vậy phải cấu hình riêng cho chiều vào và chiều ra.

Việc kết hợp Security Group và Network ACL giúp xây dựng nhiều lớp bảo vệ cho hệ thống, phù hợp với nguyên tắc **Defense in Depth** trong bảo mật.

---

## 4. Thiết kế mạng tốt giúp hệ thống dễ mở rộng

Điều mình thấy thú vị là một kiến trúc mạng được thiết kế hợp lý sẽ giúp hệ thống mở rộng dễ dàng trong tương lai.

Khi lượng truy cập tăng, chúng ta có thể:

- Thêm Amazon EC2 thông qua Auto Scaling.
- Mở rộng sang nhiều Availability Zone.
- Triển khai thêm Amazon RDS.
- Tích hợp Amazon ElastiCache.
- Triển khai Amazon ECS hoặc các dịch vụ khác mà không cần thay đổi toàn bộ kiến trúc ban đầu.

Ngoài ra, Amazon VPC còn hỗ trợ Hybrid Cloud thông qua VPN hoặc AWS Direct Connect, giúp doanh nghiệp kết nối hạ tầng tại chỗ với môi trường AWS.

---

## Điều mình rút ra sau khi tìm hiểu

Sau khi tìm hiểu Amazon VPC, mình nhận ra rằng việc triển khai một hệ thống trên AWS không chỉ đơn giản là tạo một máy chủ rồi cài đặt ứng dụng.

Một hệ thống ổn định, bảo mật và có khả năng mở rộng luôn bắt đầu từ việc thiết kế kiến trúc mạng phù hợp.

Khi nền tảng mạng được xây dựng tốt, việc triển khai các dịch vụ như Amazon EC2, Amazon RDS, Elastic Load Balancer hay Auto Scaling sẽ trở nên đơn giản, hiệu quả và an toàn hơn.

---

## Kết luận

Theo mình, Amazon VPC là một trong những dịch vụ quan trọng nhất của AWS và là nền tảng của hầu hết các kiến trúc Cloud hiện đại.

Việc hiểu rõ cách hoạt động của VPC, Subnet, Route Table, Internet Gateway, NAT Gateway, Security Group và Network ACL không chỉ giúp triển khai hệ thống đúng cách mà còn nâng cao khả năng bảo mật, mở rộng và vận hành.

Nếu đang bắt đầu học AWS hoặc chuẩn bị triển khai ứng dụng trên Cloud, mình nghĩ Amazon VPC là chủ đề nên tìm hiểu đầu tiên trước khi tiếp cận các dịch vụ khác.