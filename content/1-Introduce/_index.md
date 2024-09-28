---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Overview

The majority of our current customers utilize an on-premise **DNS** system. As resources are initialized on the AWS platform, AWS offers **DNS** services through **Amazon Route 53**. This lab focuses on creating a hybrid **DNS** system, enabling integration between your existing on-premise **DNS** system and the **DNS** service provided by **Amazon Route 53**.

#### Route 53

**Route 53** offers various **DNS** capabilities, including:
- Public **DNS** domain registration
- Creation of private **DNS** zones
- **DNS** hybrid engine
- Domain name resolution

Within Route 53, the **Route 53 Resolver** service introduces three tools to facilitate a hybrid **DNS** architecture between your on-premise **DNS** system and AWS:

1. **Outbound Endpoints**: **Route 53 Resolver** sends **DNS** queries from AWS to your on-premise **DNS** system through these endpoints.
2. **Inbound Endpoints**: These endpoints serve as targets for **DNS** queries from your on-premise **DNS** system to domains hosted on AWS.
3. **Route 53 Resolver** Rules: Utilizing Resolver Rules, you can configure Route 53 to forward **DNS** queries for specific domains to your on-premise **DNS** system.

![Route 53](/images/icon.png?width=10pc)
