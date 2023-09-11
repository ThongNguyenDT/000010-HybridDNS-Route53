---
title : "Set up Hybrid DNS with Route 53 Resolver"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Set up Hybrid DNS with Route 53 Resolver

#### Overview

The majority of existing customers own an on-premise **DNS** system. When you initialize resources on the AWS platform, AWS provides **DNS** service through **Amazon Route 53**. In this lab, we will explore building a **DNS** hybrid system that enables integration between your existing on-premise **DNS** system and the **DNS** service of **Amazon Route 53**.

#### Route 53

**Route 53** offers various **DNS** capabilities, including public **DNS** domain registration, the creation of private **DNS** zones, a **DNS** hybrid engine, and domain name resolution. Route 53 Resolver, within Route 53, can perform recursive lookups against public **DNS** systems.

Within Route 53, the Route 53 Resolver service provides three essential tools for establishing a hybrid **DNS** architecture between your on-premise **DNS** system and AWS:

- **Outbound Endpoints**: These are used for sending **DNS** queries from **Route 53 Resolver** to your on-premise **DNS** system.
- **Inbound Endpoints**: These act as targets for **DNS** queries originating from your on-premise **DNS** system to domains hosted on AWS.
- **Route 53 Resolver Rules**: This feature lets you configure Route 53 to forward **DNS** queries for specific domains to your on-premise system's DNS.

![Route 53](/images/icon.png?featherlight=false&width=10pc)

#### Content

1. [Introduction](1-introduce/)
2. [Preparation](2-prerequiste/)
3. [Connect to RDGW](3-connecttordgw/)
4. [Microsoft AD Deployment](4-setupad/)
5. [Setup DNS](5-setupyridDNS/)
6. [Resource Cleanup](6-cleanup/)
