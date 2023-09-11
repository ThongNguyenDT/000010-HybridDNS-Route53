---
title : "Create Route 53 Resolver Rules"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

#### Create Route 53 Resolver Rules

The next step involves creating **Route 53 Resolver** Rules. A **Route 53 Resolver** rule allows you to define two actions: Forward or System.

- With the Forward action, you can configure **Route 53 Resolver** to forward **DNS** queries to an external **DNS** resolver (e.g., a **DNS** server on your premises).
- With the System action, Route 53 will internally query for domain name resolution (Private **DNS** zones, VPC **DNS**, and Public **DNS**).

1. Open the **Route 53 console** using the search box and locate **Route 53**.
   - In the left sidebar, select **Rules** and then click on **Create rule**.

![RDGW](/images/5.2-CreateRoute53rule/0001.png?featherlight=false&width=90pc)

2. Fill in the following information:
   - **Name**: ForwardToOnPremAD
   - **Rule type**: Forward
   - **Domain name**: onprem.example.com. (This is the domain name of the directory you created in the previous section)
   - **VPC that uses this rule**: HybridDNS-VPCStack
   - **Outbound Endpoint**: R53-OutboundEndpoint

![RDGW](/images/5.2-CreateRoute53rule/0002.png?featherlight=false&width=90pc)

3. Under Target IP addresses, enter the two recorded **AWS Managed Microsoft Active Directory** IP addresses. Note that you need to select **Add target** to add a second IP address.

   - Click on **Submit**

![RDGW](/images/5.2-CreateRoute53rule/0003.png?featherlight=false&width=90pc)

4. Complete the process of creating the Route 53 Resolver rule.

![RDGW](/images/5.2-CreateRoute53rule/0004.png?featherlight=false&width=90pc)

5. You have now successfully configured **Route 53 Resolver** to forward queries for onprem.example.com to another **DNS** resolver (e.g., AWS Managed Microsoft AD). The domain name, onprem.example.com, simulates a **DNS** domain hosted by your **DNS** on-premise system.

![RDGW](/images/5.2-CreateRoute53rule/0005.png?featherlight=false&width=90pc)
