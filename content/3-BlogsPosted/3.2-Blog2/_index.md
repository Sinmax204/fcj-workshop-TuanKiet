---
title: "Blog 2"
date: 2026-05-17
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---



# AWS Architecture Blog | What I Learned About Amazon VPC – The Foundation of Every AWS Architecture

Hello everyone,

While learning AWS, I initially spent most of my time exploring services such as Amazon EC2, Amazon S3, and AWS Lambda. However, the more I studied and practiced, the more I realized that before deploying any application to the cloud, the most important step is not selecting a compute or storage service—it is designing a solid network architecture.

That is why I decided to learn about **Amazon Virtual Private Cloud (Amazon VPC)**, one of the core networking services provided by AWS.

---

## Architecture Overview

<p align="center">
    <img src="/Sinmax204/fcj-workshop-TuanKiet/images/3-BlogsPosted/blog2.jpg" width="100%">
</p>

<p align="center">
<i>Figure 3.2. Basic Amazon VPC architecture with Public Subnet, Private Subnet, Application Load Balancer, Amazon EC2, and Amazon RDS.</i>
</p>

---

## 1. What Is Amazon VPC?

Amazon Virtual Private Cloud (Amazon VPC) enables users to create an isolated virtual network within AWS where cloud resources such as Amazon EC2, Amazon RDS, and Application Load Balancers can be securely deployed.

A VPC can be thought of as a private data center in the cloud, giving users complete control over IP addressing, routing, and network security.

Within a VPC, users can:

- Configure a CIDR block for the virtual network.
- Create Public and Private Subnets.
- Configure Route Tables to manage traffic routing.
- Connect to the Internet using an Internet Gateway or NAT Gateway.
- Secure resources using Security Groups and Network ACLs.

In my opinion, designing the VPC is the first and most important step when building cloud infrastructure on AWS.

---

## 2. Why Separate Public and Private Subnets?

A well-designed AWS architecture usually separates resources into two network layers.

The **Public Subnet** contains Internet-facing resources such as:

- Application Load Balancer
- Bastion Host
- NAT Gateway

The **Private Subnet** contains backend resources that should not be directly accessible from the Internet, including:

- Amazon EC2 application servers
- Amazon RDS databases
- Internal application services

This separation significantly reduces the attack surface while improving the overall security of the system.

---

## 3. Security Group vs. Network ACL

When I first started learning AWS networking, I often confused Security Groups with Network ACLs. After reading the AWS documentation and experimenting with both services, I finally understood their different responsibilities.

### Security Group

- Operates at the instance level.
- Allows only explicitly permitted traffic.
- Is **stateful**, meaning return traffic is automatically allowed.

### Network ACL

- Operates at the subnet level.
- Supports both **Allow** and **Deny** rules.
- Is **stateless**, meaning inbound and outbound rules must be configured separately.

Using both Security Groups and Network ACLs together provides multiple layers of protection and follows the **Defense in Depth** security principle.

---

## 4. A Well-Designed Network Makes Scaling Easier

One of the most valuable lessons I learned is that a properly designed network architecture makes future expansion much easier.

As application traffic grows, the infrastructure can easily scale by:

- Launching additional Amazon EC2 instances using Auto Scaling.
- Expanding across multiple Availability Zones.
- Integrating Amazon RDS for managed databases.
- Adding Amazon ElastiCache to improve performance.
- Deploying containerized applications with Amazon ECS without redesigning the existing architecture.

Amazon VPC also supports Hybrid Cloud connectivity through VPN and AWS Direct Connect, making it easier for organizations to integrate on-premises infrastructure with AWS.

---

## What I Learned

After learning about Amazon VPC, I realized that deploying applications on AWS is much more than simply launching virtual machines.

A secure, reliable, and scalable cloud system always starts with a well-designed network architecture.

Once the networking foundation is in place, deploying services such as Amazon EC2, Amazon RDS, Elastic Load Balancer, and Auto Scaling becomes much simpler, more secure, and easier to manage.

---

## Conclusion

For me, Amazon VPC is one of the most important AWS services because it forms the foundation of almost every modern cloud architecture.

Understanding how VPC, Subnets, Route Tables, Internet Gateway, NAT Gateway, Security Groups, and Network ACLs work together not only helps build secure cloud environments but also improves scalability, reliability, and operational efficiency.

If you are beginning your AWS learning journey or planning to deploy applications to the cloud, I highly recommend mastering Amazon VPC before moving on to higher-level AWS services. A strong networking foundation will make learning the rest of the AWS ecosystem much easier.