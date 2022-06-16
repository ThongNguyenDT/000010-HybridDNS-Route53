---
title : "Setup DNS"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Set up **DNS**

In this lab, you'll use the three tools (**Outbound Endpoint**, Resolver Rules, and Inbound Endpoints) of **Route 53 Resolver** to set up a hybrid **DNS** for your AWS infrastructure and On-premises.

The **AWS Managed Microsoft Active Directory** service you created in the previous section will be used to simulate your **DNS** on-premise system. The following figure will show the architecture that you will continue to build on top of the infrastructure you deployed in the previous section:

![Route 53](/images/2-Pre/0005.png?featherlight=false&width=60pc)

Explain:

- **Red Arrow** – You will configure **Outbound Endpoint** to bridge **Route 53 Resolver** that can forward **DNS** queries to AWS Managed **Active Directory**.
- You will create the **Route 53 Resolver** Rule to provide instructions for forwarding **DNS** queries from **Route 53 Resolver** externally to AWS Managed **Active Directory**.
- **Blue Arrow** – You will configure the Inbound Endpoint to create a bridge for AWS Managed **Active Directory** that can forward **DNS** queries to **Route 53 Resolver**. From there, Route 53 - Resolver can forward those queries to **EC2 instances** that are acting as Remote Desktop Gateways.
- **Green arrow** – **EC2 instance** will connect to **Route 53 Resolver** using IP address VPC+2. By default, VPC+2 is the IP address for the **DNS** Resolver of the VPC. (Example: VPC CIDR in this post is 10.0.0.0/16. So, the IP address of **DNS** Resolver in VPC is 10.0.0.2).
- **Black Arrow**– **Route 53 Resolver** can forward **DNS** queries from **EC2 instance** or AWS Managed **Active Directory** to other services of AWS.

#### Content

1. [Create Route 53 Outbound Endpoint](5.1-createoe/)
2. [Create Route 53 Resolver Rules](5.2-createroute53/)
3. [Create Route 53 Inbound Endpoints](5.3-createie/)
4. [Test Result](5.4-results/)

{{% notice note %}}
Once done, you'll understand how to set up a **DNS** hybrid between **DNS** hosted zones on your on-premises system and in AWS. In the exercise, we used the AWS Managed Microsoft AD **DNS** server to simulate the **DNS** on-premise system. To visualize integration with your actual on-premise environment, you need to specify IP addresses for your **DNS** on-premise servers instead of the AWS Managed Microsoft AD * IP addresses *DNS**.
To allow your **DNS** on-premise servers to resolve any AWS Private Zones hosted on Route 53, you would create **DNS** forwarding rules in the **DNS** system on- your premises. For **DNS** domains hosted on Route 53, forward to the IP address of the Inbound Endpoint.
{{% /notice %}}