---
title : "Set up Hybrid DNS with Route 53 Resolver"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---

# Set up Hybrid DNS with Route 53 Resolver

#### Overview

The majority of existing customers own an on-premise **DNS** system. When you initialize resources on the AWS platform, AWS provides **DNS** service through **Amazon Route 53**. In this lab, we will experiment with building a **DNS** hybrid system that will allow you to integrate with your existing **DNS** on-premise system with **DNS service ** of **Amazon Route 53**.

#### Route 53

**Route 53** provides some **DNS** capabilities such as public **DNS** domain registration, the ability to create private **DNS** zones, **DNS** hybrid engine, and domain name resolution. With domain name resolution, Route 53 Resolver can perform recursive lookups against public **DNS** systems.

In Route 53, the Route 53 Resolver service provides three tools to enable a hybrid **DNS** architecture between your **DNS** on-premise system and AWS. These three tools are:

- **Outbound Endpoint**s: **DNS** queries from **Route 53 Resolver** to your **DNS** system will be sent from Outbound Endpoint**s** .
- **Inbound Endpoints**: Inbound endpoints act as targets for **DNS** queries from your **DNS** on-premise system to domains hosted on AWS.
- **Route 53 Resolver Rules**: With Route 53 Resolver Rules, you can configure Route 53 to forward **DNS** queries for your specific domains to the system DNS on-premise.

![Route 53](/images/icon.png?featherlight=false&width=10pc)

#### Content

1. [Introduction](1-introduce/)
2. [Preparation](2-prerequiste/)
3. [Connect to RDGW](3-connecttordgw/)
4. [Microsoft AD Deployment](4-setupad/)
5. [Setup DNS](5-setupyridDNS/)
6. [Resource Cleanup](6-cleanup/)