---
title: "Introduction"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---



## Amazon VPC Endpoints

Amazon VPC Endpoints enable private connectivity between resources inside a Virtual Private Cloud (VPC) and supported AWS services without requiring traffic to traverse the public Internet. By keeping communication within the AWS network, VPC Endpoints improve security, reduce latency, and simplify network architecture.

There are two common types of VPC Endpoints:

- **Gateway Endpoint:** Supports Amazon S3 and Amazon DynamoDB. It allows resources in a VPC to access these services through private routes instead of using an Internet Gateway or NAT Gateway.
- **Interface Endpoint (AWS PrivateLink):** Creates Elastic Network Interfaces (ENIs) inside a VPC, enabling private access to many AWS services and supported third-party applications.

Using VPC Endpoints is considered an AWS best practice when applications require secure communication with AWS services while remaining inside a private network.

---

## Workshop Overview

In this workshop, I will explore how Amazon VPC Endpoints provide secure and private access to AWS services.

The lab environment consists of two Virtual Private Clouds:

- **VPC Cloud:** Hosts AWS resources, including an Amazon S3 Gateway Endpoint and an EC2 instance used to verify private connectivity.
- **VPC On-Prem:** Simulates an on-premises data center. An EC2 instance configured with **strongSwan VPN** establishes a Site-to-Site VPN connection with AWS Transit Gateway, allowing the on-premises environment to communicate securely with cloud resources.

During the workshop, I will configure and verify connectivity between the simulated on-premises network and AWS services through the Gateway Endpoint. This demonstrates how organizations can securely access Amazon S3 without exposing traffic to the public Internet.

The workshop also provides practical experience with hybrid cloud networking concepts, including Site-to-Site VPN, AWS Transit Gateway, and Amazon VPC Endpoints.

---

## Workshop Architecture

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.1-Workshop-overview/diagram1.png" width="90%">
</p>

<p align="center">
<i>Figure 5.1. Workshop architecture for Amazon VPC Endpoints.</i>
</p>