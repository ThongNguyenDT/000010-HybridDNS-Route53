---
title : "Setup DNS"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---


#### Set up DNS

In this lab, you'll utilize three tools: **Outbound Endpoint**, Resolver Rules, and Inbound Endpoints from **Route 53 Resolver** to establish a hybrid **DNS** configuration for your AWS infrastructure and On-premises.

The **AWS Managed Microsoft Active Directory** service, created in the preceding section, will be employed to simulate your on-premise **DNS** system. The architecture you'll be building upon the existing infrastructure is depicted in the following figure:

![Route 53](/images/2-Pre/0005.png?width=60pc)

#### Explanation

- **Red Arrow**: Configure an **Outbound Endpoint** to link **Route 53 Resolver** for forwarding **DNS** queries to the AWS Managed **Active Directory**.

- Establish a **Route 53 Resolver** Rule to direct **DNS** queries from **Route 53 Resolver** externally to AWS Managed **Active Directory**.

- **Blue Arrow**: Set up an Inbound Endpoint to bridge AWS Managed **Active Directory** for forwarding **DNS** queries to **Route 53 Resolver**. Subsequently, Route 53 Resolver can further route these queries to **EC2 instances** acting as Remote Desktop Gateways.

- **Green Arrow**: **EC2 instances** will connect to **Route 53 Resolver** using the IP address VPC+2, which is the default IP address for the **DNS** Resolver of the VPC. (For instance, if VPC CIDR is 10.0.0.0/16, the **DNS** Resolver's IP address in the VPC is 10.0.0.2).

- **Black Arrow**: **Route 53 Resolver** can forward **DNS** queries from **EC2 instances** or AWS Managed **Active Directory** to other AWS services.

#### Content

1. [Create Route 53 Outbound Endpoint](5.1-createoe/)
2. [Create Route 53 Resolver Rules](5.2-createroute53/)
3. [Create Route 53 Inbound Endpoints](5.3-createie/)
4. [Test Result](5.4-results/)

> **Note:** Upon completion, you will comprehend how to establish a hybrid **DNS** configuration between **DNS** hosted zones on your on-premises system and within AWS. During the exercise, we utilized the AWS Managed Microsoft AD **DNS** server to mimic the on-premise **DNS** system. To visualize integration with your actual on-premise environment, replace the IP addresses of your on-premise **DNS** servers with those of the AWS Managed Microsoft AD **DNS**.

> To enable your on-premise **DNS** servers to resolve AWS Private Zones hosted on Route 53, you would create **DNS** forwarding rules within your on-premise **DNS** system. For **DNS** domains hosted on Route 53, forward to the IP address of the Inbound Endpoint.
