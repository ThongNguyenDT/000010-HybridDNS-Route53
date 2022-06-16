---
title : "Create Route 53 Resolver Rules"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

#### Create Route 53 Resolver Rules

The next step is to create **Route 53 Resolver** Rules. **Route 53 Resolver** rule allows to define two actions: Forward or System.

- With Forward, you can configure **Route 53 Resolver** to forward **DNS** queries to an external **DNS** resolvers (eg **DNS** server on- your premise).
- With System, Route 53 will query internally for domain name resolution (Private **DNS** zones, VPC **DNS**, and Public **DNS**).

1. Go to **Route 53 console** through the search box and find **Route 53**.
   - In the left sidebar, select **Rules** and select **Create rule**.

![RDGW](/images/5.2-CreateRoute53rule/0001.png?featherlight=false&width=90pc)

2. Enter the following information:
   - **Name**: ForwardToOnPremAD
   - **Rule type**: Forward
   - **Domain name**: onprem.example.com. (This is the domain name of the directory you created in the previous section)
   - **VPC that use this rule**: HybridDNS-VPCStack
   - **Outbound Endpoint**: R53-OutboundEndpoint

![RDGW](/images/5.2-CreateRoute53rule/0002.png?featherlight=false&width=90pc)

3. In the Target IP addresses, enter the two recorded **AWS Managed Microsoft Active Directory** IP addresses. Note, you need to select Add target to add a second IP address.

   - Select **Submit**

![RDGW](/images/5.2-CreateRoute53rule/0003.png?featherlight=false&width=90pc)

4. Finish creating Route 53 Resolver


![RDGW](/images/5.2-CreateRoute53rule/0004.png?featherlight=false&width=90pc)

5. You have now configured **Route 53 Resolver** to forward queries for onprem.example.com to another **DNS** resolver (eg AWS Managed Microsoft AD). The domain name, onprem.example.com, simulates a **DNS** domain hosted by your **DNS** on-premise system.

![RDGW](/images/5.2-CreateRoute53rule/0005.png?featherlight=false&width=90pc)