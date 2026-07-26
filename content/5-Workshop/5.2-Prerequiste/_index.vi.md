---
title: "Điều kiện chuẩn bị"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

# Điều kiện chuẩn bị

Trước khi bắt đầu workshop, cần chuẩn bị môi trường AWS và đảm bảo tài khoản có đầy đủ quyền để triển khai các tài nguyên phục vụ quá trình thực hành.

---

## Cấp quyền IAM

Để triển khai và dọn dẹp các tài nguyên được tạo trong workshop, tài khoản AWS cần được gán một **IAM Policy** với đầy đủ các quyền cần thiết.

Chính sách này cho phép thao tác với nhiều dịch vụ AWS như:

- AWS CloudFormation
- Amazon EC2
- Amazon VPC
- Amazon S3
- AWS Lambda
- AWS IAM
- Amazon Route 53
- AWS Systems Manager (SSM)
- Amazon CloudWatch
- AWS Secrets Manager

Sau khi tạo IAM Policy, tiến hành gán chính sách cho IAM User hoặc IAM Role sử dụng để thực hiện workshop.



---

## Triển khai hạ tầng bằng AWS CloudFormation

Để giảm thời gian cấu hình thủ công, workshop sử dụng **AWS CloudFormation** để tự động tạo toàn bộ hạ tầng cần thiết.

Workshop được triển khai tại Region:

- **US East (N. Virginia) – us-east-1**

Mở liên kết CloudFormation được cung cấp, sau đó thực hiện các bước sau:

1. Giữ nguyên các tham số mặc định.
2. Đánh dấu xác nhận các điều khoản.
3. Chọn **Create stack** để bắt đầu triển khai.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/create-stack1.png" width="90%">
</p>

<p align="center">
<i>Hình 5.2. Tạo CloudFormation Stack.</i>
</p>

---

Tiếp theo, tích chọn hai ô xác nhận quyền tạo tài nguyên AWS rồi nhấn **Create stack**.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/create-stack2.png" width="90%">
</p>

<p align="center">
<i>Hình 5.3. Xác nhận và bắt đầu triển khai CloudFormation Stack.</i>
</p>

---

## Hoàn tất quá trình triển khai

Sau khi tạo Stack, CloudFormation sẽ tự động triển khai toàn bộ hạ tầng. Quá trình này mất khoảng **15 phút**.

Khi trạng thái của Stack chuyển sang **CREATE_COMPLETE**, môi trường thực hành đã sẵn sàng để sử dụng.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/complete.png" width="90%">
</p>

<p align="center">
<i>Hình 5.4. CloudFormation Stack được triển khai thành công.</i>
</p>

---

## Kiểm tra các tài nguyên đã tạo

Sau khi CloudFormation hoàn tất, hệ thống sẽ tự động tạo các tài nguyên cần thiết cho workshop.

### Hai Amazon VPC

CloudFormation tạo hai mạng VPC để mô phỏng môi trường **AWS Cloud** và **On-Premises**, phục vụ việc thiết lập kết nối thông qua Site-to-Site VPN và VPC Endpoint.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/vpcs.png" width="90%">
</p>

<p align="center">
<i>Hình 5.5. Hai Amazon VPC được tạo tự động.</i>
</p>

---

### Ba Amazon EC2 Instance

Ngoài hai VPC, hệ thống còn tạo ba máy chủ EC2 phục vụ cho việc cấu hình VPN, kiểm tra kết nối và xác thực việc truy cập Amazon S3 thông qua VPC Endpoint.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/ec2.png" width="90%">
</p>

<p align="center">
<i>Hình 5.6. Các EC2 Instance được tạo để phục vụ workshop.</i>
</p>

---

