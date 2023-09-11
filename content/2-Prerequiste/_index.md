---
title : "Preparation "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Preparation

#### Overview

Your initial task involves setting up the network infrastructure in AWS. In this segment, you will make use of **AWS Quick Start** to construct a secure and highly available (HA) network infrastructure. Additionally, you will deploy an instance of **AWS Managed Microsoft Active Directory** using **AWS Directory Service** to emulate your on-premises **DNS** system. Upon completing this stage, you will have successfully implemented the subsequent infrastructure architecture:

![Set up](/images/2-Pre/0001.png?featherlight=false&width=60pc)

#### **AWS Quick Starts**

**AWS Quick Starts** stands as a collection of architectural templates created by **Solution Architects and AWS Partners**. These templates employ **AWS CloudFormation** as the underlying tool to build the architectures outlined within them.

#### **AWS CloudFormation**

**AWS CloudFormation** represents AWS's service for **Infrastructure as Code (IaC)**, enabling the creation of infrastructure based on templates written in either **YAML** or JSON format. A designated **template** is uploaded to the CloudFormation service, which then automatically generates the infrastructure as defined in the template.

#### **AWS Directory Service**

**AWS Directory Service** provides a mechanism to deploy an **Active Directory** directly on the AWS Cloud, streamlining management tasks and granting end-user access to AWS services.

#### **Content**

1. [Generate Key Pair](2.1-createkeypair/)
2. [Initiating CloudFormation Template](2.2-launchcloudformation/)
3. [Security Group Configuration](2.3-security/)
