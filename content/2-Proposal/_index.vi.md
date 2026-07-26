---
title: "Bản đề xuất"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---



# Smart Health Management System

## Hệ thống quản lý sức khỏe trên nền tảng điện toán đám mây AWS

### 1. Tóm tắt đề xuất

Smart Health Management System là một nền tảng quản lý sức khỏe được xây dựng trên Amazon Web Services (AWS), nhằm cung cấp một hệ thống có khả năng mở rộng, tính sẵn sàng cao và bảo mật. Hệ thống hỗ trợ quản lý thông tin người dùng, hồ sơ bệnh án, các chức năng của ứng dụng và đảm bảo khả năng truy cập ổn định thông qua kiến trúc Cloud Native.

Frontend được phát triển bằng React và lưu trữ trên Amazon S3, sau đó được phân phối thông qua Amazon CloudFront. Backend được triển khai trên các máy chủ Amazon EC2 nằm sau Application Load Balancer và Auto Scaling Group nhằm tự động mở rộng khi lưu lượng truy cập tăng. Dữ liệu được lưu trữ trên Amazon RDS PostgreSQL, kết hợp với Amazon ElastiCache (Redis) để tăng tốc truy xuất dữ liệu. Ngoài ra, hệ thống còn tích hợp AWS Lambda, Amazon SQS, Amazon SNS, Amazon SES và Amazon CloudWatch để xử lý tác vụ nền, gửi thông báo và giám sát toàn bộ hệ thống.

---

## 2. Tuyên bố vấn đề

### Vấn đề hiện tại

Nhiều hệ thống quản lý hiện nay vẫn được triển khai trên hạ tầng truyền thống hoặc chỉ sử dụng một máy chủ duy nhất, dẫn đến nhiều hạn chế như:

- Khả năng mở rộng thấp khi số lượng người dùng tăng.
- Hệ thống dễ gặp điểm lỗi duy nhất (Single Point of Failure).
- Hiệu năng giảm khi lưu lượng truy cập lớn.
- Khó giám sát và xử lý sự cố.
- Bảo mật chưa đáp ứng các yêu cầu của ứng dụng Internet.

### Giải pháp đề xuất

Dự án xây dựng hệ thống Smart Health trên nền tảng AWS nhằm:

- Đảm bảo tính sẵn sàng cao thông qua Auto Scaling Group và Application Load Balancer.
- Tăng tốc truy cập bằng Amazon CloudFront.
- Bảo vệ ứng dụng với AWS WAF.
- Lưu trữ dữ liệu trên Amazon RDS PostgreSQL.
- Tăng hiệu năng bằng Amazon ElastiCache (Redis).
- Giám sát hệ thống với Amazon CloudWatch.
- Xử lý bất đồng bộ bằng AWS Lambda, Amazon SQS, Amazon SNS và Amazon SES.

---

## 3. Kiến trúc giải pháp

Hệ thống được xây dựng theo mô hình nhiều tầng nhằm đảm bảo khả năng mở rộng, hiệu năng và bảo mật.

### Mô tả kiến trúc

Người dùng truy cập website thông qua Amazon Route 53.

Các nội dung tĩnh được phân phối bởi Amazon CloudFront và bảo vệ bởi AWS WAF trước khi lấy dữ liệu từ Amazon S3.

Các yêu cầu đến hệ thống được chuyển qua Application Load Balancer, sau đó phân phối đến các máy chủ Amazon EC2 trong Auto Scaling Group.

Amazon RDS PostgreSQL chịu trách nhiệm lưu trữ dữ liệu của hệ thống, trong khi Amazon ElastiCache (Redis) lưu trữ dữ liệu tạm nhằm giảm tải cho cơ sở dữ liệu.

AWS Lambda, Amazon SQS, Amazon SNS và Amazon SES xử lý các tác vụ nền, gửi thông báo và email. Amazon CloudWatch theo dõi hoạt động của toàn bộ hệ thống để phát hiện và cảnh báo khi xảy ra sự cố.

### Sơ đồ kiến trúc

![Sơ đồ kiến trúc hệ thống Smart Health](/Sinmax204/fcj-workshop-TuanKiet/images/2-Proposal/system-architecture.jpg)
---

## Các dịch vụ AWS sử dụng

| Dịch vụ | Mục đích |
|----------|----------|
| Amazon Route 53 | Quản lý tên miền |
| Amazon CloudFront | Phân phối nội dung |
| AWS WAF | Bảo vệ ứng dụng Web |
| Amazon S3 | Lưu trữ giao diện React |
| Application Load Balancer | Cân bằng tải |
| Amazon EC2 | Chạy Backend |
| Auto Scaling Group | Tự động mở rộng |
| Amazon RDS PostgreSQL | Cơ sở dữ liệu |
| Amazon ElastiCache (Redis) | Bộ nhớ đệm |
| AWS Lambda | Xử lý tác vụ nền |
| Amazon SQS FIFO | Hàng đợi thông điệp |
| Amazon SNS | Gửi thông báo |
| Amazon SES | Gửi Email |
| Amazon CloudWatch | Giám sát hệ thống |
| Gateway VPC Endpoint | Kết nối riêng đến Amazon S3 |
| Amazon VPC | Hạ tầng mạng |

---

## 4. Triển khai kỹ thuật

### Giai đoạn 1 – Thiết kế hạ tầng

- Nghiên cứu kiến trúc AWS.
- Thiết kế VPC.
- Cấu hình IAM và Security Group.
- Thiết kế sơ đồ kiến trúc hệ thống.

### Giai đoạn 2 – Triển khai hạ tầng

- Khởi tạo Amazon EC2.
- Cấu hình Auto Scaling Group.
- Cấu hình Application Load Balancer.
- Triển khai Amazon RDS PostgreSQL.
- Thiết lập Amazon ElastiCache.

### Giai đoạn 3 – Triển khai ứng dụng

- Build ứng dụng React.
- Triển khai lên Amazon S3.
- Cấu hình Amazon CloudFront.
- Cấu hình chứng chỉ SSL với AWS Certificate Manager.
- Cấu hình Route 53.

### Giai đoạn 4 – Giám sát và xử lý sự kiện

- Thiết lập Amazon CloudWatch.
- Triển khai AWS Lambda.
- Cấu hình Amazon SQS FIFO.
- Thiết lập Amazon SNS.
- Thiết lập Amazon SES.

### Giai đoạn 5 – Kiểm thử và đưa vào vận hành

- Kiểm thử chức năng.
- Kiểm thử hiệu năng.
- Tối ưu hệ thống.
- Hoàn thiện tài liệu.
- Triển khai môi trường Production.

---

## 5. Lộ trình thực hiện

| Tuần | Nội dung |
|------|----------|
| Tuần 1 | Làm quen với AWS và Amazon EC2 |
| Tuần 2 | Amazon VPC |
| Tuần 3 | Amazon S3 |
| Tuần 4 | Amazon RDS |
| Tuần 5 | AWS Lambda |
| Tuần 6 | Amazon CloudWatch |
| Tuần 7 | AWS IAM |
| Tuần 8 | Amazon ECS & Amazon ECR |
| Tuần 9 | AWS CloudFormation |
| Tuần 10 | AWS CI/CD |
| Tuần 11 | Route 53 và Elastic Load Balancer |
| Tuần 12 | Hoàn thiện và triển khai hệ thống Smart Health |

---

## 6. Ước tính chi phí

Trong quá trình phát triển, dự án chủ yếu sử dụng các dịch vụ nằm trong AWS Free Tier.

Các dịch vụ được sử dụng gồm:

- Amazon EC2
- Amazon RDS PostgreSQL
- Amazon S3
- Amazon CloudFront
- Amazon Route 53
- AWS WAF
- Amazon ElastiCache
- AWS Lambda
- Amazon CloudWatch
- Amazon SQS
- Amazon SNS
- Amazon SES

Chi phí thực tế sẽ phụ thuộc vào mức sử dụng tài nguyên sau khi vượt giới hạn Free Tier.

---

## 7. Đánh giá rủi ro

### Các rủi ro có thể xảy ra

- Máy chủ EC2 gặp sự cố.
- Cơ sở dữ liệu ngừng hoạt động.
- Lưu lượng truy cập tăng đột biến.
- Chi phí AWS vượt dự kiến.
- Các cuộc tấn công vào ứng dụng Web.

### Biện pháp giảm thiểu

- Sử dụng Auto Scaling Group.
- Cấu hình Application Load Balancer.
- Sao lưu tự động Amazon RDS.
- Triển khai AWS WAF.
- Thiết lập cảnh báo bằng Amazon CloudWatch.
- Theo dõi chi phí bằng AWS Budgets.

---

## 8. Kết quả mong đợi

Sau khi hoàn thành dự án, hệ thống sẽ:

- Triển khai thành công Smart Health Management System trên nền tảng AWS.
- Đảm bảo tính sẵn sàng cao và khả năng mở rộng.
- Cải thiện hiệu năng thông qua Redis Cache.
- Đảm bảo an toàn cho ứng dụng bằng các dịch vụ bảo mật của AWS.
- Giám sát và cảnh báo hệ thống theo thời gian thực.
- Nâng cao kỹ năng thiết kế, triển khai và quản trị hạ tầng điện toán đám mây theo mô hình thực tế.