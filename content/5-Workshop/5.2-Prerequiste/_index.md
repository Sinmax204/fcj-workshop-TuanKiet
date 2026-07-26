---
title: "Prerequisite"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

# Prerequisite

Before starting the workshop, the AWS environment must be prepared and the required permissions must be granted to deploy the infrastructure used throughout the lab.

---

## IAM Permissions

To create and remove the AWS resources used in this workshop, the AWS account must have an **IAM Policy** with sufficient permissions.

The policy grants access to several AWS services, including:

- Amazon EC2
- Amazon VPC
- AWS CloudFormation
- Amazon S3
- AWS Lambda
- AWS Identity and Access Management (IAM)
- Amazon Route 53
- AWS Systems Manager (SSM)
- Amazon CloudWatch
- AWS Secrets Manager

After creating or updating the IAM policy, attach it to the IAM User or IAM Role that will be used during the workshop.

> **Note:** The workshop policy grants broad permissions for learning purposes. In production environments, AWS recommends following the **Principle of Least Privilege** by granting only the permissions required for each workload.

---

## Deploying the Infrastructure with AWS CloudFormation

To simplify the setup process, this workshop uses **AWS CloudFormation** to automatically provision all required resources.

The workshop is deployed in the following AWS Region:

- **US East (N. Virginia) – us-east-1**

Open the provided CloudFormation template and perform the following steps:

1. Keep all default parameters.
2. Acknowledge the required permissions.
3. Choose **Create stack** to begin the deployment.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/create-stack1.png" width="90%">
</p>

<p align="center">
<i>Figure 5.2. Creating a CloudFormation stack.</i>
</p>

---

Next, confirm the required acknowledgements and click **Create stack** to start provisioning the resources.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/create-stack2.png" width="90%">
</p>

<p align="center">
<i>Figure 5.3. Confirming the deployment and creating the CloudFormation stack.</i>
</p>

---

## Completing the Deployment

The CloudFormation deployment takes approximately **15 minutes** to complete.

Once the stack status changes to **CREATE_COMPLETE**, the workshop environment is ready for use.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/complete.png" width="90%">
</p>

<p align="center">
<i>Figure 5.4. CloudFormation stack deployed successfully.</i>
</p>

---

## Verifying the Provisioned Resources

After the deployment is completed, CloudFormation automatically creates all resources required for the workshop.

### Two Amazon VPCs

Two Virtual Private Clouds (VPCs) are created to simulate both the AWS Cloud environment and an on-premises environment for hybrid networking.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/vpcs.png" width="90%">
</p>

<p align="center">
<i>Figure 5.5. Two Amazon VPCs created by CloudFormation.</i>
</p>

---

### Three Amazon EC2 Instances

CloudFormation also provisions three Amazon EC2 instances used to configure the VPN connection and verify private connectivity to Amazon S3 through a VPC Endpoint.

<p align="center">
<img src="/Sinmax204/fcj-workshop-TuanKiet/images/5-Workshop/5.2-Prerequisite/ec2.png" width="90%">
</p>

<p align="center">
<i>Figure 5.6. Amazon EC2 instances created for the workshop.</i>
</p>

---

After completing these steps, the workshop environment is fully prepared. The next sections will focus on configuring **Amazon VPC Endpoints**, **AWS Transit Gateway**, and **Site-to-Site VPN** to enable secure private connectivity between the simulated on-premises environment and AWS services.