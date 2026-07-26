---
title: "Blog 1"
date: 2026-05-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---



# AWS Architecture Blog | What I Learned About Event-Driven Architecture with Amazon SQS and AWS Lambda

During my AWS learning journey, I realized that not every client request needs to be processed immediately. If every request is handled directly by the backend server, the application can easily become overloaded when traffic increases.

AWS provides an effective Event-Driven Architecture by combining **Amazon API Gateway**, **Amazon SQS**, **AWS Lambda**, **Amazon DynamoDB**, **Amazon CloudWatch**, and **Amazon SNS**. This architecture improves scalability, reliability, and system flexibility.

## Architecture Overview

<p align="center">
    <img src="/Sinmax204/fcj-workshop-TuanKiet/images/3-BlogsPosted/blog1.jpg" width="100%">
</p>

<p align="center">
<i>Figure 3.1. Event-Driven Architecture using Amazon API Gateway, Amazon SQS, AWS Lambda, DynamoDB, CloudWatch and Amazon SNS.</i>
</p>

---

## 1. Amazon API Gateway Receives Client Requests

When a client sends a request, Amazon API Gateway receives the HTTP request and immediately places a message into Amazon SQS instead of sending it directly to the backend application.

This approach reduces backend workload and prevents requests from being lost during traffic spikes.

---

## 2. Amazon SQS Acts as the Message Queue

Amazon SQS temporarily stores incoming messages until they are processed.

One advantage of SQS is that it completely decouples request handling from business processing. Even if thousands of requests arrive simultaneously, messages remain safely stored inside the queue and are processed one by one.

---

## 3. AWS Lambda Processes Messages Automatically

Whenever a new message appears in the queue, AWS Lambda is automatically triggered.

Lambda can perform business logic, validate data, save information into Amazon DynamoDB, or communicate with other AWS services without managing any servers.

This serverless approach reduces operational costs because compute resources are used only when events occur.

---

## 4. Amazon CloudWatch Monitors the Entire System

After Lambda finishes processing, logs and metrics are automatically sent to Amazon CloudWatch.

CloudWatch allows developers to monitor application performance, detect errors, and create alarms when metrics such as processing time, error count, or resource utilization exceed predefined thresholds.

CloudWatch Alarms can also trigger Amazon SNS to notify administrators through Email, SMS, or collaboration platforms such as Slack.

---

## Lessons Learned

From studying this architecture, I learned that introducing a message queue significantly improves system reliability and scalability.

Instead of processing every request immediately, components communicate through asynchronous events. This makes the system easier to scale, maintain, and recover from traffic spikes.

The combination of Amazon SQS and AWS Lambda also follows modern cloud-native design principles by separating producers from consumers and enabling serverless event processing.

---

## Conclusion

Amazon SQS and AWS Lambda provide an excellent example of an Event-Driven Architecture on AWS.

By integrating Amazon API Gateway, Amazon SQS, AWS Lambda, Amazon DynamoDB, Amazon CloudWatch, and Amazon SNS, developers can build applications that are scalable, reliable, and easy to monitor.

Learning this architecture helped me better understand how modern cloud applications handle asynchronous workloads and why Event-Driven Design has become one of the most widely adopted architectural patterns in AWS.