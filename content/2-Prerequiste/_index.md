---
title : "Preparation "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Preparation 

#### Overview

Your first step will be to build the network infrastructure in AWS. In this section, you will leverage **AWS Quick Start** to build a secure and highly available network infrastructure (HA). You will then deploy one more **AWS Managed Microsoft Active Directory** using **AWS Directory Service** to simulate your **DNS** on-prem system. When you complete this section, you will have successfully deployed the following infrastructure architecture:

![Set up](/images/2-Pre/0001.png?featherlight=false&width=60pc)

#### **AWS Quick Starts**

**AWS Quick Starts** is a library of architectural templates built by **Solution Architects and AWS Partners**. **AWS Quick Starts** uses **AWS CloudFormation** as the engine to build the architectures written in its templates.

#### **AWS CloudFormation**

**AWS CloudFormation** is AWS's **Infrastructure as Code (IaC)** service that allows you to create template-based infrastructure (written in **YAML** or JSON). **Template** is uploaded to the CloudFormation service and automatically generates the infrastructure described in the template.

#### **AWS Directory Service**

**AWS Directory Service** is a tool that allows you to deploy an **Active Directory** right on AWS Cloud to simplify management and provide end-user access to AWS services.

#### **Content**

1. [Generate Key Pair](2.1-createkeypair/)
2. [Starting CloudFormation Template](2.2-launchcloudformation/)
3. [Security Group Configuration](2.3-security/)