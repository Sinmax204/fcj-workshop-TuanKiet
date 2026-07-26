---
title: "Proposal"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---



# Smart Health Management System

## A Scalable and Highly Available Healthcare Platform on AWS

### 1. Executive Summary

The Smart Health Management System is a cloud-based healthcare platform designed to simplify medical record management, appointment scheduling, and healthcare service delivery. The application is deployed on Amazon Web Services (AWS) using a highly available and scalable architecture following the AWS Well-Architected Framework.

The frontend is developed with React and hosted on Amazon S3, while Amazon CloudFront accelerates content delivery worldwide. Backend services run on Amazon EC2 instances managed by an Auto Scaling Group behind an Application Load Balancer. Amazon RDS PostgreSQL stores application data, and Amazon ElastiCache for Redis improves system performance through caching. AWS CloudWatch provides monitoring, while AWS Lambda, Amazon SQS, Amazon SNS, and Amazon SES support asynchronous processing and notification services.

---

## 2. Problem Statement

### Current Challenges

Many healthcare management systems are still deployed on a single server or traditional infrastructure, resulting in several limitations:

- Limited scalability during peak usage.
- Single point of failure.
- Slow response time under heavy workloads.
- Difficult monitoring and maintenance.
- Insufficient protection against common web attacks.

### Proposed Solution

The Smart Health Management System leverages AWS cloud services to provide:

- High availability using Auto Scaling Group and Application Load Balancer.
- Fast global content delivery through Amazon CloudFront.
- Secure web application protection using AWS WAF.
- Reliable relational database with Amazon RDS PostgreSQL.
- High-performance caching using Amazon ElastiCache for Redis.
- Centralized monitoring and logging using Amazon CloudWatch.
- Event-driven processing with AWS Lambda, Amazon SQS, Amazon SNS, and Amazon SES.

---

## 3. Solution Architecture

The system architecture consists of multiple AWS services working together to provide scalability, security, and reliability.

### Architecture Overview

The user accesses the Smart Health website through Amazon Route 53. Static web resources are delivered by Amazon CloudFront, protected by AWS WAF, and served from Amazon S3.

API requests are forwarded to an Application Load Balancer, which distributes traffic across multiple Amazon EC2 instances running inside private subnets. Auto Scaling automatically launches or terminates EC2 instances based on system load.

Application data is stored in Amazon RDS PostgreSQL, while frequently accessed data is cached in Amazon ElastiCache for Redis to reduce database workload.

Supporting services such as AWS Lambda, Amazon SQS, Amazon SNS, and Amazon SES handle background jobs, notifications, and asynchronous processing. Amazon CloudWatch continuously monitors the entire infrastructure.

### Architecture Diagram

![System Architecture](/Sinmax204/fcj-workshop-TuanKiet/images/2-Proposal/system-architecture.jpg)
---

## AWS Services Used

| Service | Purpose |
|---------|---------|
| Amazon Route 53 | Domain Name System (DNS) |
| Amazon CloudFront | Global Content Delivery Network |
| AWS WAF | Web Application Firewall |
| Amazon S3 | Host React frontend and application files |
| Application Load Balancer | Traffic distribution |
| Amazon EC2 | Backend application servers |
| Auto Scaling Group | Automatic scaling |
| Amazon RDS PostgreSQL | Relational database |
| Amazon ElastiCache (Redis) | In-memory cache |
| AWS Lambda | Background processing |
| Amazon SQS FIFO | Message queue |
| Amazon SNS | Notification service |
| Amazon SES | Email service |
| Amazon CloudWatch | Monitoring and logging |
| Gateway VPC Endpoint | Secure private S3 access |
| Amazon VPC | Network isolation |

---

## 4. Technical Implementation

### Phase 1 – Infrastructure Planning

- Design the AWS architecture.
- Configure VPC, subnets, route tables, and security groups.
- Prepare IAM roles and permissions.

### Phase 2 – Core Infrastructure Deployment

- Deploy Amazon EC2 instances.
- Configure Auto Scaling Group.
- Configure Application Load Balancer.
- Deploy Amazon RDS PostgreSQL.
- Configure Amazon ElastiCache.

### Phase 3 – Frontend Deployment

- Build the React application.
- Upload static files to Amazon S3.
- Configure Amazon CloudFront.
- Configure HTTPS using AWS Certificate Manager.
- Configure Route 53 DNS.

### Phase 4 – Monitoring and Event Processing

- Configure Amazon CloudWatch dashboards and alarms.
- Deploy AWS Lambda functions.
- Configure Amazon SQS FIFO queues.
- Configure Amazon SNS notifications.
- Configure Amazon SES email service.

### Phase 5 – Testing and Deployment

- Perform functional testing.
- Conduct performance testing.
- Optimize infrastructure.
- Complete project documentation.
- Deploy the production environment.

---

## 5. Timeline & Milestones

| Week | Activities |
|------|------------|
| Week 1 | AWS Fundamentals and EC2 |
| Week 2 | Amazon VPC |
| Week 3 | Amazon S3 |
| Week 4 | Amazon RDS |
| Week 5 | AWS Lambda |
| Week 6 | Amazon CloudWatch |
| Week 7 | AWS IAM |
| Week 8 | Amazon ECS & Amazon ECR |
| Week 9 | AWS CloudFormation |
| Week 10 | AWS CI/CD |
| Week 11 | Route 53 and Elastic Load Balancer |
| Week 12 | Smart Health System Deployment and Final Presentation |

---

## 6. Budget Estimation

The project primarily utilizes AWS Free Tier resources during development.

Estimated AWS services include:

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

Actual costs depend on resource consumption after exceeding AWS Free Tier limits.

---

## 7. Risk Assessment

### Potential Risks

- EC2 instance failure.
- Database failure.
- Traffic spikes.
- Unexpected AWS costs.
- Security attacks.

### Mitigation Strategy

- Enable Auto Scaling Group.
- Configure Application Load Balancer.
- Enable automatic RDS backups.
- Deploy AWS WAF.
- Configure CloudWatch alarms.
- Enable AWS Budgets and billing alerts.

---

## 8. Expected Outcomes

Upon completion, the project will deliver:

- A fully functional Smart Health Management System running on AWS.
- High availability with automatic scaling.
- Secure and reliable infrastructure.
- Faster application performance through Redis caching.
- Real-time monitoring using Amazon CloudWatch.
- Practical experience in designing, deploying, and managing enterprise cloud infrastructure on AWS.