---
title: "Blog 1"
date: 2026-05-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---



# AWS Architecture Blog | Điều mình học được về kiến trúc Event-Driven với Amazon SQS và AWS Lambda

Trong quá trình tìm hiểu AWS, mình nhận ra rằng không phải mọi yêu cầu từ người dùng đều cần được xử lý ngay lập tức. Nếu tất cả request đều được xử lý trực tiếp bởi Backend thì khi lượng truy cập tăng cao, hệ thống rất dễ bị quá tải và ảnh hưởng đến hiệu năng.

Một trong những mô hình phổ biến trên AWS để giải quyết vấn đề này là **Event-Driven Architecture**. Bằng cách kết hợp **Amazon API Gateway**, **Amazon SQS**, **AWS Lambda**, **Amazon DynamoDB**, **Amazon CloudWatch** và **Amazon SNS**, hệ thống có thể xử lý yêu cầu linh hoạt hơn, tăng khả năng mở rộng và nâng cao độ ổn định.

## Kiến trúc tổng quan

<p align="center">
   <img src="/Sinmax204/fcj-workshop-TuanKiet/images/3-BlogsPosted/blog1.jpg" width="100%">
</p>

<p align="center">
<i>Hình 3.1. Kiến trúc Event-Driven sử dụng Amazon API Gateway, Amazon SQS, AWS Lambda, Amazon DynamoDB, Amazon CloudWatch và Amazon SNS.</i>
</p>

---

## 1. Amazon API Gateway tiếp nhận yêu cầu từ người dùng

Khi người dùng gửi một yêu cầu đến hệ thống, Amazon API Gateway sẽ tiếp nhận request và chuyển dữ liệu vào hàng đợi Amazon SQS thay vì xử lý trực tiếp.

Theo mình, cách tiếp cận này giúp giảm tải cho Backend và đảm bảo các yêu cầu không bị mất ngay cả khi lượng truy cập tăng đột biến.

---

## 2. Amazon SQS đóng vai trò là hàng đợi thông điệp

Amazon SQS chịu trách nhiệm lưu trữ các message trong hàng đợi để chờ xử lý.

Điểm mình thấy hữu ích là SQS giúp tách biệt hoàn toàn giữa thành phần tiếp nhận yêu cầu và thành phần xử lý nghiệp vụ. Khi hệ thống nhận được nhiều request cùng lúc, các message vẫn được lưu trữ an toàn trong Queue và xử lý tuần tự, giúp hạn chế tình trạng quá tải.

Ngoài ra, nếu quá trình xử lý gặp lỗi nhiều lần, message có thể được chuyển sang **Dead-Letter Queue (DLQ)** để dễ dàng kiểm tra và xử lý sau.

---

## 3. AWS Lambda xử lý dữ liệu tự động

Khi có message mới trong Amazon SQS, AWS Lambda sẽ tự động được kích hoạt để xử lý.

Lambda có thể thực hiện nhiều tác vụ như:

- Xử lý dữ liệu.
- Kiểm tra tính hợp lệ của thông tin.
- Lưu dữ liệu vào Amazon DynamoDB.
- Gọi các dịch vụ AWS khác khi cần thiết.

Theo mình, đây là một trong những ưu điểm lớn của mô hình Serverless vì không cần quản lý máy chủ, chỉ sử dụng tài nguyên khi có yêu cầu nên giúp tối ưu chi phí vận hành.

---

## 4. Amazon CloudWatch giám sát toàn bộ hệ thống

Sau khi Lambda hoàn thành xử lý, toàn bộ Logs và Metrics sẽ được gửi về Amazon CloudWatch.

CloudWatch hỗ trợ:

- Theo dõi hiệu năng của hệ thống.
- Thu thập Logs.
- Giám sát thời gian xử lý.
- Theo dõi số lượng lỗi.
- Thiết lập cảnh báo khi các chỉ số vượt ngưỡng.

Khi có sự cố xảy ra, CloudWatch Alarm có thể kích hoạt Amazon SNS để gửi thông báo qua:

- Email
- SMS
- Slack
- Các dịch vụ thông báo khác

Điều này giúp quản trị viên nhanh chóng phát hiện và xử lý sự cố.

---

## Điều mình rút ra sau khi tìm hiểu

Sau khi tìm hiểu kiến trúc này, mình nhận thấy việc sử dụng hàng đợi (Queue) giúp hệ thống hoạt động ổn định hơn rất nhiều khi lượng truy cập tăng cao.

Thay vì xử lý toàn bộ request ngay lập tức, các thành phần trong hệ thống giao tiếp với nhau thông qua các sự kiện (Event). Điều này giúp giảm sự phụ thuộc giữa các dịch vụ, tăng khả năng mở rộng và giúp việc bảo trì trở nên đơn giản hơn.

Bên cạnh đó, việc kết hợp Amazon SQS với AWS Lambda còn giúp tận dụng tối đa mô hình Serverless, vừa tiết kiệm chi phí vừa đảm bảo khả năng mở rộng theo nhu cầu thực tế.

---

## Kết luận

Đối với mình, Amazon SQS kết hợp với AWS Lambda là một ví dụ điển hình về kiến trúc Event-Driven trên AWS.

Việc kết hợp Amazon API Gateway, Amazon SQS, AWS Lambda, Amazon DynamoDB, Amazon CloudWatch và Amazon SNS giúp xây dựng một hệ thống có khả năng mở rộng cao, hoạt động ổn định và dễ dàng giám sát.

Qua bài viết này, mình hiểu rõ hơn cách các ứng dụng hiện đại xử lý các tác vụ bất đồng bộ trên nền tảng AWS và vì sao Event-Driven Architecture đang trở thành một trong những mô hình được sử dụng phổ biến trong các hệ thống Cloud hiện nay.